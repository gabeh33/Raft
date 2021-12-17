Readme for Gabe Holmes project 6, distributed key-value store. This project proved to be much more difficult for me than any of the previous projects. When I started
out I wanted to make sure I had a very good understanding of Raft. This involoved reading the paper and watching a few videos on how elections and log replication
worked. After this I was able to implement a simple election, and respond to put() requests by storing information just on the leader. Knowdlege on how to format and 
send key-value pairs from previous projects was quite useful. I followed the implementation approach recommended in the project description. This means after 
implementing elections I moved on to actually replicating data and only committing it when the cluster was able to reach a consensus. This proved to be the 
most challenging part and took the longest. I was able to commit when a consensus was reached, but it took me a long time to realize that I was not committing 
on the replicas. There were times where I decided to take a slightly different approach than the paper said, but I always ended up coming back to exactly what the paper
outlines. Once I was able to replicate data, I moved on to dealing with lossy connections. This also proved to be very challenging, but eventually I came up with
a method where if consensus is not reached in a certain amount of time, the leader sends the exact same message that it received from a client back to itself. This 
proved to work and while it is not the most efficient, it will work every time on lossy connections. I then implemented the smaller changes in 5.4.1 and 5.4.2. 
Running the simulator on my local machine I was able to pass 15/17 tests and the vast majority of performance tests.  
