学习

- Topic
  - Description
  - Why designed/implemented this way
  - Tradeoff/alternative



## 2025年9月

9.8 (周一)

学习 Redis

- How does the sentinel get updated info of the primary/replica servers it's monitoring?

  - Sentinel sends command `INFO` to both the primary and replica servers, during its periodic loop when an server instance is “due” (by default it's 10s, but under certain cases, liker a replica is objectively down, we will send command more often, by every 1s). The full call path is `serverCron` in the server.c file, which calls `sentinelTimer` when `server.sentinel_mode` is turned on, then calls function `sentinelHandleDictOfRedisInstances`, which runs on all 3 types of primary/replica/sentinel instances. Inside the function, `sentinelHandleRedisInstance` is run on each individual instance, which calls `sentinelSendPeriodicCommands` (this is where the routine period commands like `PING`, `INFO`, `PUBLISH` are sent) and `sentinelCheckSubjectivelyDown`.

- How does sentinel discover replicas?

  - As mentioned above, sentinel sends periodic `INFO` comamnd and then parse the `replication` section to learn about replicas. The output text looks like this:

    ```
    role:master
    connected_slaves:1
    slave0:ip=127.0.0.1,port=6381,state=online,offset=12345,lag=1
    ```

    And then it will print a log `+slave slave 127.0.0.1:6381 127.0.0.1 6381 @ mymaster 127.0.0.1 6379`. 
    
    Notice that sentinel will also discover other sentinels.

- What's the difference between `master_replid` and `master_replid2`?

  - These two replicaition IDs are used in Redis partial sync. `master_replid` is the current replication ID, while  `master_replid2` is the previous ID kept around to handle those replicas slightly lagged behind in sync. Every time the primary updates its replication ID, the current `master_replid` will be moved into `master_replid2`, and `second_replid_offset` is set to the primary's current replication offset (which will later be used to compare against `replica_replid_offset` to check if the replica is close enough to the primary to allow partial sync).
  - In theory, we might even keep more historical IDs like  `master_replid3`, `master_replid4`, etc., but such design will complicate the overall logic a lot without much benefit.



## 2025年8月

8.31

学习

- Learned how Redis inserts a new key-value pair of strings into memory.

  - After the client sends the key-value pair to Redis server, the key and the value are stored as `sds` (simple dynamic string) objects, which are kinda similar to C style null-terminated strings but actually are *length-prefixed* buffers that also keep a trailing `0x0` for C-API compatibility. There're different types of `sds` and headers, and in my case I use `SDS_TYPE_8` since the key-value isn't huge in size.

    - ```c
      struct __attribute__ ((__packed__)) sdshdr8 {
          uint8_t len; /* used */
          uint8_t alloc; /* excluding the header and null terminator */
          unsigned char flags; /* 3 lsb of type, 5 unused bits */
          char buf[];
      };
      ```

  - During insertion, the function `kvobjCreateEmbedString` calculates the required size of both the key and value by adding up the size of header (`sdshdr8` in my case), payload and 1 byte of null terminator. Then `malloc` (could be either glibc malloc or  jemalloc) is called to assign memory to the new `robj`. Then `memcpy` is called to copy the key and value to the newly assigned position and now we have a complete `robj`. Finally, this new node is linked to the dict of the database by using the `dictEntryLink` object previously retrieved by doing search in `dbFindByLink` (the same function used to look up the `setCommand` object prior to processing the command).



8.30

学习

- Learned how Redis finds the corresponding command that user makes.

  - Say user's client sends  `set mykey myvalue`, Redis server would parse the string to get the command's name `"set"`, and then search for this key in the dictionary of all commands, which is a collection of many linked lists. In the `dictFindLink` and `dictFindLinkInternal` functions, after applied to the hash function, key `"set"` gets its index 211, and we can retrieve the targeted linked list from `commandsDict->ht_tables[0][211]`. Each node in the linked list is a `dictEntry` object as follows.

    - ```c
      // src/dict.c
      struct dictEntry {
          void *key;
          union {
              void *val; uint64_t u64; int64_t s64; double d;
          } v;
          struct dictEntry *next;  /* Next entry in the same hash bucket. */
      };
      ```

  - Redis traverses the entire linked list to find the target key `"set"` and returns the corresponding `redisCommand` object, which contains a lot of metadata about this command, like summary, time complexity description, etc. The  `redisCommandProc` field is the actual implementation of the command.

  - I was planning to understand how to actually insert the user key and value into Redis, but I was just too slow and inefficient and thus only explored fetching the `setCommand` object.



8.29

学习

- Read Redis' documents to learn various data structures like strings, hashes, sets, lists, sorted sets, but I haven't dived deep into the implementations yet.
- Went through all syscalls invovled when running `strace sleep`. The only business logic is just `clock_nanosleep(CLOCK_REALTIME, 0, {tv_sec=30, tv_nsec=0}` while the other syscalls are common Linux process setup and reading locale files like `openat(AT_FDCWD, "/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3`.



8.26 (周二)

学习

- How Redis fetches data.
  - Once the server receives the get request from the client, it looks at the command type and then calls `getCommand`  and `getGenericCommand(client)` to process the request, then `lookupKeyRead(client->db, key);` . Once the value is retrieved, `addReplyBulk`  is called, and the background running IO thread would detect such new reply and call  `sendReplyToClient` . Finally the client gets the value it wants.
  - Note: I don't understand much about Redis's networking, single-thread model, and internal data structures yet.



8.25 (周一)

学习

- How RocksDB fetches data from memtable.
  - A user wants to retrieve the value for a given key, and thus creates an empty`std::string`  to pass its pointer into `DB::Get` function, and then to `DBImpl::Get` by default, then `DBImpl::GetImpl`. Once RocksDB finds the corresponding memtable by the given column family, the emtpy string pointer gets passed to `MemTable::Get`, `MemTable::GetFromTable`, and then saved in a `Saver` instance, a helper class which stores all intermediate info. Then the default `SkipListRep` creates an iterator to seek the key that the user is interested in, the underlying `InlineSkipList::GreaterOrEqual` gets called to search for target, which traverses from the head node, using each node object's `next_` field to jump to the next node and then comparing the node's key (directly placed in memory slot right after `next_` field , rather than stored as a class member) with the target. Once the value is retrieved, the callback function `SaveValue` is called to put  it into the previous `Saver` object. And since the `Saver` object stores the address of the originally empty user-provided string, now that string variable finally contains the value the user is looking for.





## End of file