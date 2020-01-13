## Overview
The project aims to create and evaluate Chord, a cloud overlay network algorithm with convergent hashing using our own Akka/HTTP-based simulator.

In this course project, we will solidify the knowledge of resilient overlay networks by designing and implementing a simulator of a cloud computing facility, specifically a reliable overlay network using the Chord algorithm for distribution of work in a cloud datacenter. Our goal is to gain experience with the fundamentals of distributed hash tables (DHTs) and we will experiment with resource provisioning in the cloud environment. We have implemented a cloud simulator in Scala using Akka actors and built and run our project using the SBT with the runMain command from the command line. In the simulator, we created the following entities and defined interactions among them: actors that simulate users who enter and retrieve data from the cloud, actors who represent servers (i.e., nodes) in the cloud that store the data, and case classes that represent data that are sent to and retrieved from the cloud. 

##Prerequisites
- SBT


#Run through SBT
- `sbt "run numberOfComputersOrNodes numberOfRequests`

## Functionality

1) We take number of nodes and number of requests from command prompt
2) We dynamically choose the value of m (the number of bits taken from the hash ) based on the number of nodes.
3) Node values are then chosen from the hash value using sha-1 hashing of unique strings simmilar to IP addresses assigned to each node.
4) Then we initialize the network by creating nodes using akka actors representing each node in the network ,each node having its own finger table.
5) The movies are then distributed onto the network following the rule that any node cannot have more than O(keys/nodes) entries.
6) Then for every request, the movie string is converted into m bit hash string and then passed onto the network. Then lookup finishes once the movie is found on the network else a null result is returned instead.
5) After the network stabilization we start file requests with random keys between (0,2^m) using a ticker of 1 second delay from each node ,each node firing number of requests equal to the number of request from command prompt. 
6) We get the output as average number of hops per request.

The project is still a work in progress and has been tried to be done in retrospective manner. But still the project requires a few more additions. 


