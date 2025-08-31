## 2025年8月

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