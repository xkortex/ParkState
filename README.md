# ParkState
A place to park your state. An experiment in event sourcing, CRDTs, distributed log replication, and learning Scala for fun and profit 

Yeah the name is a bit silly. It's a working title, also this is experimental :). 
**keywords**: 
scala, event sourcing, CRDT, distributed, log replication, kv, immutable radix trie, hybrid logical clock

### 9000-foot-view:
A distributed key-value store based on immutable radix tries and event sourcing. Every transaction is 
associated with a [hybrid logical clock](https://jaredforsyth.com/posts/hybrid-logical-clocks/) ([pdf](http://www.cse.buffalo.edu/tech-reports/2014-04.pdf)),
such that every event has a strict ordering, even in a distributed system. 

This isn't aiming for performance but it *is* aiming for reliability and consistency. 