# notes

general purpose brain dump. 

## links and research: 
https://jaredforsyth.com/posts/hybrid-logical-clocks/
https://muratbuffalo.blogspot.com/2014/07/hybrid-logical-clocks.html
[CRDTs: The hard parts](https://www.youtube.com/watch?v=x7drE24geUw)


Vague overview / blueprint: 
Data is stored in an immutable radix tree/prefix tree/ trie. This has some restrictions:
- keys are `Identifier`s (UTF strings, match `[a-zA-Z_]\w*`) for maximum compatibility
- nodes can be leaves or branches but not both (if `/foo/bar` is a leaf, you can't create `/foo/bar/spam`, or it overwrites)
- a keypath is a tuple of `Identifier`s, but can readily be split from `/`-separated-paths  

Architecture ideas: 
- Data payload is always bytes, msgpack-encoded
- Mutation events are stored in an array holding `HLClock`, `TreeRoot`, and the transaction
- Transactions are stored in an LRU for rapid access of recently set values
- Something something blockchain/Merkle tree
- Topology consists of servers (Leader +2/4 followers) and Agents. 
- I have no idea how garbage collection or durability is going to work but that'll be 
 fun to figure out. CRDTs video has some neat ideas on how to compact the log
- I'd like to use gRPC and/or QUIC for comms. That might be a lot to bite off at once so 
 maybe start with TCP & HTTP
  
