### Summary

We are going to implement a distributed, high performant, concurrent, in-memory  hash-table.  We will be testing the code on Intel Xeon Phi coprocessors (Latedays cluster).

### Background

The applications of hash-table in real world applications are countless. Hash tables allow constant time lookups. 

Cuckoo hashing is a scheme in computer programming for resolving hash collisions of values of hash functions in a table, with worst-case constant lookup time. According to Wikipedia, the name derives from the behavior of some species of cuckoo, where the cuckoo chick pushes the other eggs or young out of the nest when it hatches; analogously, inserting a new key into a cuckoo hashing table may push an older key to a different location in the table.

Having entire hashtable in one node is infeasible in many large-scale scenarios. The memory required to store entire hashmap might not be enough for one node. Also, accessing hashmap on a  single node can become a bottleneck from the performance perspective. Hence, arises the need to have a distributed in-memory hashmap, without compromising on the performance.  

### Challenges

The primary challenge of this project is gaining a sufficient understanding of the Cuckoo hashing and possibilities of parallelising it. Also, scaling the hashtable to multiple nodes should a difficult task. 

### Resources

We will be running and testing our code on Latedays cluster machine. Our code base will start from the scratch but also rely on paper on MemC3 [1] for a single node. 

### Goals and Deliverables

Plan to achieve 
Sequential implementation of the Hashmap on a single node.
Parallel implementation of in-memory hashmap using cuckoo hashing.
Scaling this hashtable in distributed environment.
	
	
Hope to achieve 
Dynamically remapping keys and generating in-memory hashtable to prevent a single node becoming a hotspot. Later, even this load balancer can be replicated to avoid a single bottleneck.
On a single node, hashtable might grow exponentially to not fit in the memory of the system. We will try to optimise disk I/O with in-memory cuckoo hashing.
Applying this disk I/O trick in distributed environment. 


### Platform Choice

We will implement our project in C++ and will be using latedays for testing and development. However, the solution will be generic enough so that it can run on any x86 platform.  

### Schedule

- 4/10 - 4/16: Do literature survey and implement sequential hashtable on a single node.
- 4/17 - 4/24: Implement basic version in-memory hashmap using cuckoo hashing for a single node.
- 4/25 - 5/1: Complete and optimise in-memory hashmap using cuckoo hashing for a single node.
- 5/2 - 5/8: Scaling this hashtable in distributed environment.
- 5/9 - 5/11: Final optimisation and report preparation.

### References

[1] https://www.cs.cmu.edu/~dga/papers/memc3-nsdi2013.pdf
