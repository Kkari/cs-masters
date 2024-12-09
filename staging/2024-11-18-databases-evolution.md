By the way, one thing that I have seemed to learn about the evolution of Databases in general:
 
There were a few mental leaps:
The Relational Model was a very successful mental leap on how to compose databases because it was so much more efficient than the older pointer based architectures. 
In the nineties people realised the efficiency of column storage over row storage for aggregate processing, which was a huge performance benefit. Interestingly this shift was pushed by business requirements because that was the first time in history that OLTP systems gathered enough data so that people wanted to start analysing them. 
There are micro-advancements:
Better Buffer Pool mechanisms, cache eviction algorithms, query planners are giving a thousand 1% improvements.  
And there are the hardware and vendor folks. Sometimes they come out with a new gadget that challenges all the assumptions we had about system design so far. 
Traditional wisdom said that network is the slowest in a system. With modern DC networking actually network is faster than a HDD, so in-memory replication might bet a better persistence mechanism than saving to disc.
Traditional wisdom said that the best warehouse architecture is to have nodes distribute the data in a shared nothing architecture and rebalance them as new nodes are added. Objects store like S3 completely changed the game and made the separation of compute and storage the new paradigm. 
SSDs are a massive win of course, they are still a lot slower though than RAM, but it is also a game changer. Especially because they employ a different block structure, so you have to re-optimise the block access algorithms to take full advantage of their speed and not to trash them too quickly with write workloads. Their write behaviour amortises them more quickly on a block level.
S3 and even SSD and HDDs are built-in basic query capabilities to prevent moving data from the nodes.
There was this Intel chip that was discontinued which was a persistent RAM called Optane. That would have been a massive game-changer if they manage to make production profitable. 