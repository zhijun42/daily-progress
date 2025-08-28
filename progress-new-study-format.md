## 2025年8月

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