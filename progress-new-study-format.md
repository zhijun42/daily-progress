学习

- Topic
  - Description
  - Why designed/implemented this way
  - Tradeoff/alternative



## 2025年10月

10.20 (周一)

Reading the Redis cluster spec document

- `MOVED` redirection shows that the specific key is being served at the other node, and then client should update its slot map and go straight to the new node next time (no ASKING needed). `ASK` redirection shows there's ongoing slot migration and the key asked isn't served on this node anymore and the client should talk to the migration destination node to do the operation. Notice that the next time the client makes a new query about the same slot, the query should still go to the source node first because we don't know if the migration is done, and the destination node during resharding will handle a query only if it comes with an `ASKING` command, which proves that the client had already tried talking to the source node.
- Say we're migrating a slot from source node A to destination node B.
  - All queries about existing keys are processed by node A.
    - If the key still exists on node A, the operation will be handled.
    - If the key doesn't exist on node A, the client will get an `ASK` redirection to have node B handle the query.
  - All queries about new keys in node A will be prompted to talk to node B via an  `ASK` redirect, so that we won't be creating any new keys in node A and eventually we can finish migrating all keys in the slot to node B.
  - If there're multiple keys and some keys are in node A while others are in node B, caught in the middle of migration), node B (not sure, perhaps node A) will get generate a `-TRYAGAIN` error.



10.16 (周四)

Last month, I learned how Redis inserts a new key-value pair of strings into the database. Today I learned how Valkey does that, and it's different from Redis because Valkey implemented a new internal structure `hashtable` in late 2024:

```c
struct hashtable {
    hashtableType *type;
    ssize_t rehash_idx;        /* -1 = rehashing not in progress. */
    bucket *tables[2];         /* 0 = main table, 1 = rehashing target.  */
    size_t used[2];            /* Number of entries in each table. */
    int8_t bucket_exp[2];      /* Exponent for num buckets (num = 1 << exp). */
    int16_t pause_rehash;      /* Non-zero = rehashing is paused */
    int16_t pause_auto_shrink; /* Non-zero = automatic resizing disallowed. */
    size_t child_buckets[2];   /* Number of allocated child buckets. */
    void *metadata[];
};
```

while Redis has been using the `dict` structure:

```c
struct dict {
    dictType *type;
    dictEntry **ht_table[2];
    unsigned long ht_used[2];
    long rehashidx; /* rehashing not in progress if rehashidx == -1 */
    /* Keep small vars at end for optimal (minimal) struct padding */
    unsigned pauserehash : 15; /* If >0 rehashing is paused */
    unsigned useStoredKeyApi : 1; /* See comment of storedHashFunction above */
    signed char ht_size_exp[2]; /* exponent of size. (size = 1<<exp) */
    int16_t pauseAutoResize;  /* If >0 automatic resizing is disallowed (<0 indicates coding error) */
    void *metadata[];
};

struct dictEntry {
    struct dictEntry *next;  /* Must be first */
    void *key;               /* Must be second */
    union {
        void *val;
        uint64_t u64;
        int64_t s64;
        double d;
    } v;
};
```

Essentially these two are quite similar, just using different mechanisms to implement a hashtable, although I don't understand both enough to talk about the tradeoffs yet.

In Valeky, both setting an exisiting key and adding a new key will call the function `void setKey(client *c, serverDb *db, robj *key, robj **valref, int flags)`, which then calls

- `static void dbSetValue(serverDb *db, robj *key, robj **valref, int overwrite, void **oldref)`
- or `static void dbAddInternal(serverDb *db, robj *key, robj **valref, int update_if_existing)`.

correspondingly. Eventually the new value (an `robj` ) object will be created, with the key (if it's short enough) embedded into it. For exaxmple, the object with key "short-key-01" and value "another-kinda-long-value" has these fields:

```
 type = {unsigned int:4} 0 [0x0]
 encoding = {unsigned int:4} 8 [0x8]
 lru = {unsigned int:24} 15856960 [0xf1f540]
 hasexpire = {unsigned int:1} 0 [0x0]
 hasembkey = {unsigned int:1} 1 [0x1]
 refcount = {unsigned int:30} 1 [0x1]
 ptr = {void *} 0x60000151d162
```

and looks like this in memory:

```
   80 40 f5 f1   06 00 00 00   │ ·@······ │
   62 d1 51 01   00 60 00 00   │ b·Q··`·· │
   01 60 73 68   6f 72 74 2d   │ ·`short- │
   6b 65 79 2d   30 31 00 18   │ key-01·· │
   1d 01 61 6e   6f 74 68 65   │ ··anothe │
   72 2d 6b 69   6e 64 61 2d   │ r-kinda- │
   6c 6f 6e 67   2d 76 61 6c   │ long-val │
   75 65 00 00   00 00 00 00   │ ue······ │
```

Since the field `hasembkey` is true, the bytes immediately following the object is the key string. And I find a trick to manually access a specific database entry once I'm inside the debugger of a running Valkey server:

```
(robj *)client->db->keys->hashtables[slot_number]->tables[table_index]->entries[entry_index]
```

 A `bucket` obejct is the container that eventually stores these `robj` objects. And the functions `dbSetValue` and `dbAddInternal` above are just about searching for a specific bucket and insert position inside it.



10.14 (周二)

I would like to read the TCP module in the Linux source code to better understand how the TCP networking protocol is implemented in real life. I'd like to do this in my IDE with code analysis enabled to facilitate reading the code. At first, I thought the IDE has mainly three components read, write and run the code, but I was wrong because reading and writing the code are the same from the IDE's perspective, because they both require code analysis (find usage/declaration, auto complete, refactoring, etc), which means I would have to do enough configuration to allow my IDE to parse the Linux source code.

There're two options of setting up the project. The first is to set it as a Makefile project, but CLion couldn't build targets successfully (although I'm not entirely sure which specific Makefile target is required, exactly. I tried `prepare` and faield) due to some missing Linux-specific files like `elf.h`. 

The second option is to set it up as a compilation database project, which only requires a `compile_commands.json` file. However, to generate such file, I would still need to build the project (I'm not sure if there's a way to somehow "dry run" the compile commands), which would fail due to the reason above. So I did a hack - I used my AWS EC2 Ubuntu machine to build the source code via `make -j"$(nproc)" compile_commands.json` and then stole the output, as well as some directories (like `arch/x86/`, `net/ipv4` ), otherwise I would fail at missing files like `asm/compiler.h`. failed

Then I needed to manually edit the build flags in each entry in the compile_commands.json file because apparently they are only compatible with the environment on my EC2 and not my MacOS to avoid errors like  `clang: error: unknown argument: '-fno-allow-store-data-races'` and `clang: error: invalid argument 'kernel' to -mcmodel=`. Honetly I don't fully understand this part, becaue according to Jetbrains CLion doc, the IDE just needs to extract all the necessary compiler information, such as include paths and compilation flags, and it shouldn't need to actually run the long `gcc` command. So why should it care about whether a flag is legal? Perhaps it's trying to tell me if I had build my source code the right way. This is where things are tricky - I just intend to **READ the code**, but CLion will try to make all features available, which is not their fault though. 

Eventually I got entries like this in the DB json file, which finally allows me to view the TCP congestion control file `tcp_cong.c` smoothly with code analysis enabled.

```
{
  "command": "gcc -Wp,-MMD,net/ipv4/.tcp_cong.o.d -nostdinc -I./arch/x86/include -I./include ... -c -o net/ipv4/tcp_cong.o net/ipv4/tcp_cong.c",
  "directory": "/Users/zhijunliao/Engineering/reading/c/linux",
  "file": "/Users/zhijunliao/Engineering/reading/c/linux/net/ipv4/tcp_cong.c"
},
```



10.13 (周一)

Networking

- Learned about TCP end-to-end congestion control where the TCP host doesn't have explicit feedback on the network congestion conditions and can only infer from observing the network behaviors like packet loss/delay/ACK. Each TCP host has a dynamic congestion window that updates frequently, and throughout the TCP connection the gap between the last byte sent and last byte ACK must lie within this window. So, TCP host can change this window size to implicitly change the rate it sends packets into the network, based on the latest congestion conditions. Also learned about the RFC 5681 algorithm which contains 3 parts: slow start, congestion avoidance and fast recovery.



10.12 (周日)

- Finished writing the article on using `strace` and `tcpdump` to dig into what's behind a simple HTTP GET request. I interpreted all raw bytes in the packets captured by `tcpdump` , which is great for learning IPv4 header (20 bytes), UDP header (8 bytes), TCP header (40 bytes), DNS query response (A records), etc.



10.10 (周五)

Working on Redis sentinel

- Cleaned up all code changes and finally post the pull request in the Redis repo. Since this issue also exists in Valkey, I also post a PR there, although I just submit the changes of refactoring sentinel test design to allow spinning up two clusters to make it easier for code review. Both PRs have comprehensive descriptions.
- I looked back at the original Github issue where cluster A changed IP address and later the same IP address got reassigned to cluster B, causing problems. I generally understood the issue but then I started thinking more about the details. I assume all redis servers should each run on a single machine (that is, it won't be like my local development environment where I have multiple redis processes running on different ports on my computer) at the default port 6379. Now after cluster A changed IP, what would the sentinel A do? If it didn't know the new IP of cluster A, it would fail to connect with any server in cluster A and thus believed the master is objectively down and there started a failover, which would fail of course because no slave could be reached, and such failover would keep on going on endless epochs.
  - I'm not sure if this is what happens. An alternative is that sentinel A actuall knew the new IP address of all servers in cluster A, and yet it still remembered the old IP (I don't know the exact workflow of leading to such situation. If sentinel still members the old IP of the master, it will definitely find it dead and start a failover, like I describe above). Then a slave server in cluster B got reassigned an IP from cluster A, or maybe all servers in cluster B did so.
  - What I know for sure is that there was a oscillation pattern where two sentinel groups both believe a slave instance belongs to them and thus alternate sending `replicaof` commands to it in `+fix-slave-config` events. I also believe there's an event of `+convert-to-slave` when the sentinel tried to convert the slave that got mistakenly promoted as new master back to slave again. However, I can't put together the full picture of what happened exactly. Perhaps that's okay and I'm just being pedantic trying to figure out all details and steps.
  - Notice that my pull request will only solve the problem of promoting the wrong candidate slave, but it can't directly address the oscillation pattern, which is due to the flaw in the sentinel design where sentinels can only discover more slave instances, and wouldn't prune any one out.



10.1 (周三)

Working on Redis sentinel

- I solved the sentinel sticky belief issue (sentinels still believe server 30006 is a slave of mymaster 30000 even after I have the server successfully sync with the second master 30005) by running `SENTINEL RESET "mymaster"` command, which would remove server 30006 as slave and only add back the four servers 30001 ~ 30004.
- I ran into a data race issue in 02-slaves-reconf.tcl test where a slave now has a new master (we can tell from the INFO output) but the sentinel still believe it's following the old master. The reason is: the `+slave-reconf-sent` and `+slave-reconf-inprog` events proceeded, but the  `+slave-reconf-done` event was never reached because the new master went down (as requested by the test suite) too quickly and the slave immediately marks `master_link_status` as DOWN according to the its INFO command output. The sentinel should have refreshed INFO more frequently so I did that to fix the issue, but I'm not sure if the data race is eliminated for all devices and environments.
- I also ran into flakiness in my 04-slave-selection.tcl test case "Cannot failover when there's no good slave". The expected correct ordering is the following: [2]. the slave in the second cluster updates replid after following the master in the first cluster; [3]. sentinels monitoring this slave instance notices the new replid 3. manual failover starts. If step 3 happens before 2, this test case would fail. The only way to eliminate the data race is to wait until the sentinels update the replication ID of the server 30006 instance of the second cluster (notice that now each sentinels stores server 30006 twice in their memory because they see this server in two clusters) to match with the first cluster before starting failover (notice that it's not enough for the server 30006 to sync replication ID, we have to strictly wait until the sentinels see such change - remember that the sentinels are always lagged behind the reality, by design). Unfortunately I don't know how to achieve this in the given design of sentinel commands, unless I add a new command/functionality.
- I ran into another raace in my 04-slave-selection.tcl test "Slave selection works when the master reboots immediately" where the slave server 30006 couldn't be selected after master 30005 rebooted and shut down. I didn't figure out why yet.
- I enriched the state flag `is_relevant_to_master` from binary to 3 values: REPLID_UNVERIFIED, REPLID_RELEVANT and REPLID_NOT_RELEVANT. And when function `sentinelSelectSlave` runs and sees this field as unintialized, it will compute the flag on the fly. It's possible that the sentinel has just detected the slave instance and hasn't got the chance to verify its replication ID before the failover process starts.





## 2025年9月

9.30 (周二)

Working on Redis sentinel

- My guardrail logic caused flakiness in 00-base.tcl test. The master would go down and reboot immediately, and repeat such process multiple times, getting assigned a completely new replid, different from slaves's. GPT's previous strategy of keeping cached replid in the sentinel states doesn't work well because I think it's not possible to properly decide when changing the cached replid field. Apparently we can't update it every time the master has a new replid. We might consider updating it sometime (e.g. 10s) after the master finishes reboot, but the exact logic feels complicated and gives me headaches. I came up with a new idea: stop using cached replid and add a new `is_relevant` field to the slave instance state. This field gets assigned new value every time the sentinel receives INFO from the slave, but this flag won't change to 0 immediately when the sentinel detects a mismatch between the master and the slave - instead, the sentinel would wait some time if the master just rebooted.
- The 00-base.tcl test not only crashes the master multiple times, but also crashes the majority of the sentinel instances, and thus wipes out all the INFO memories of these sentinels. I had been struggling trying to fix the edge cases caused by such complicated situation, and then I realized that I shouldn't perform so such testing in the simple 00-base.tcl file. Each test case is meant to be simple and specific to certain source code (a function, a workflow, etc) but I had been actually trying to create a comprehensive test on the overall sentinel design. I should specifically test my slave selection guardrail logic in 04-slave-selection.tcl file.
- In my 04-slave-selection.tcl test, I successfully set up two cluster. I manually ask the slave 30006 in the second cluster to follow the master 30000 in the first cluster (so that I can test now it's no longer a proper candidate when the second master fails over), and then ask the slave to follow the second master 30005 back (this time the failover should succeed). This works well and I intend to add more tests (specifically, the edge cases from 00-base.tcl earlier where the master goes down and reboots immediately), but then I find out sentinels believe the new master 30006 in the second cluster still follow the master 30000 and they detect 30006 believes it's a master (which is true), so sentinels send a `slaveof` command to change 30006 back to slave to follow 30000. Now everything is just messed up. The underlying problem is that once the sentinel finds a redis instance is a replica of another instance, it will hold on to such belief forever until the master instance in is reset due to failover process. I need to figure out a way to not mess up two clusters.



9.24 (周三)

Working on Redis sentinel

- I was able to refactor the current sentinel test design to allow spinning up two master-slave cluster. Previously there has been only one master "mymaster" with 4 slaves.
  - Here is my failed attempt: Edit `tests/sentinel/run.tcl` to spawn 2 more instances, and make one of them become a separate new master via `slaveof no one` command and make the other one the slave of it. This didn't work because during `init-tests.tcl`, function  `create_redis_master_slave_cluster`  will be called to turn all 7 redis server instances into a single cluster. Even if I tried to send manual `slaveof` command later, sentinel monitoring the cluster would detech such divergence and revert my instances back to slaves.
  - Another failed attempt: This time I made use of the given 5 instances and stole 2 of them to become the new cluster via manual `slaveof` commands. This also wouldn't work due to sentinel monitoring and correcting.
  - Here is the new/correct approach: I refactor the `init-tests.tcl` file to move all operations into TCL functions because they would need to be called twice - once for "mymaster", second for the new master. Essentially, we can treat it like the original `init-tests.tcl` gets called twice. I define a global flag `set ::setup_second_master 1` in my test file `04-slave-selection.tcl` to control this behavior.
- Now I have a new working cluster of a new master with a slave. I convert the slave to follow the default "mymaster" instead, so that it will have new replication ID and I can verify my guardrail logic of checking replication ID before promoting slaves. Once this is done, I revert my slave back to follow its original master, and this time the failover will succeed because the replication ID matches. This is how I implement the testing logic.
- My guardrail logic broke the existing `12-master-reboot.tcl` test because when a master goes down and reboots immediately (carries a new replid) to load data, all slaves can't talk to it to update their replid and thus can't be promoted as expected, failing the test. Initially I was hoping that once the master finishes loading, all slaves can now sync to get new replid and thus be selected as new master, but I didn't realize that once the master gets back fully functioning, it's no longer objectively down from sentinels' perspective and thus failover isn't needed any more.





9.16 (周二)

学习 Redis

- The overall testing framework is designed around one single primary-replica cluster. The file `tests/instances.tcl` contains a lot of utilities around. During testing setup, we usually run `spawn_instance` to spin up sentinel and redis servers, and then add them to global variables `::sentinel_instances` and `::redis_instances`. Relevant helper functions like `foreach_sentinel_id` , `foreach_redis_id`, `R` (send command to an instance) etc, rely on these two states. Even the final `cleanup` step relies on this design to kill all running processes and remove temp directories.
  - I'm trying to add a guardrail to verify the replication ID before promoting a replica to become the new primary. Adding this guardrail is straightforward, but adding test would require spinning up two primary-replica clusters, which is nearly impossible to do in the current testing framework and would likely require much refactoring (probably not worthwhile).



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