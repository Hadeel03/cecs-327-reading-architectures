* Ghadeer Al Jufout
* Simon Zhang

1. What is a three-tiered client-server architecture?
    * A three-tiered client-server is a server that may sometimes act as a client, each layer on a separate machine, and being a client and also being a server at the same time
    **It separates the application into three layers:**
        1. The Presenation layer (client)
        2. Application login layer (server)
        3. Data layer (server)
    * Each of these layers is run on a separate node. The client layer is responsible for user interactions. The application login layer will handel the logic of the application. Lastly, the data layer is responsible for managing the data and its storage. 

2. What is the difference between a vertical distribution and a horizontal distribution?
    * Vertical distribution is achieved by placing logically different components on different machines (adding resources such as CPU and storage to an already existing node); horizontal distribution is a client or server may be physically split up into logically equivalent parts, but each part is operating on its own share of the complete data set, thus balancing the load (instead of adding resources to a single node, horizontal involves adding whole new nodes). 

3. If a client and a server are placed far apart, we may see network latency dominating overall performance. How can we tackle this problem?
    * Instead of synchronous communication, where the client waits for the server's response before proceeding, use asynchronous communication. This allows the client to continue performing other tasks while waiting for the server's response. This can be achieved by using callbacks, promises, or async/await patterns, depending on the programming language or framework.

4. Consider a chain of processes $P_{1}, P_{2}, \ldots, P_{n}$ implementing a multitiered client-server architecture. Process $P_{i}$ is client of process $P_{i}+1$, and $P_{i}$ will return a reply to $P_{i}-1$ only after receiving a reply from $P_{i}+1$. What are the main problems with this organization when taking a look at the request-reply performance at process $P_{1}$?

    * The main issues are cumulative latency, dependency, and failure impact.

    -- Cumulative Latency: Each request-reply interaction between successive layers adds to latency, which is particularly problematic with a large number of tiers (n).

   -- Dependency and Failure Impact: Performance at P1 is directly affected by the responsiveness and reliability of all intermediate processes (P2 to Pn). Failure or poor performance of any tier can degrade P1's performance immediately.

5. In a structured overlay network, messages are routed according to the topology of the overlay. What is an important disadvantage of this approach?
    An important disadvantage is that neighboring nodes in the overlay network might be physically far apart, leading to long physical paths for message routing, despite appearing as short logical paths in the overlay network.

6. Consider an unstructured overlay network in which each node randomly chooses $c$ neighbors. If $P$ and $Q$ are both neighbors of $R$, what is the probability that they are also neighbors of each other?
    * probability that they are also neighbors of each other is c/N-1. Consider the follwoing:
    - Node R will randomly chooses c neighbors from N-1 possible nodes. 
    - Given P & Q are both neighbors of R, and so the selection will be random. 
    - The probability any certain node is a neighbor of another certain node is c/N-1. And so the probability that P & Q are also neighbors of each other c/N-1. 
    
7. Not every node in a peer-to-peer network should become superpeer. What are reasonable requirements that a superpeer should meet? 
 * Some of the requirements a superpeer should meet: 
    1. Expected to be **long-lived process with high availability.** 
    2. There should be **backup schemes** that can be deployed incase of any unstable behavior of a superpeer.
    3. Superpeers should be **evenly distributed** across the overlay network.
    4. Superpeers **should not serve more than a fixed number of nodes.** 

8. Give an example of a self-managing system in which the analysis component is completely distributed or even hidden.

    * P2P can be an example of self-managing system.In P2P networks, each peer acts both as a client and as a server, sharing files directly with other peers without relying on a centralized server. The analysis of available files, their distribution, and the management of network resources are typically decentralized and handled autonomously by each peer. 

9. Consider a BitTorrent system in which each node has an outgoing link with a bandwidth capacity $B_{out}$ and an incoming link with bandwidth capacity $B_{in}$. Some of these nodes (called seeds) voluntarily offer files to be downloaded by others. What is the maximum download capacity of a BitTorrent client if we assume that it can contact at most one seed at a time?

    * The maximum download capacity of a BitTorrent client would be Bout,because each seed in the BitTorrent system offers files to be downloaded by others. The maximum download speed a client can achieve is limited by the upload speed of the seed it is connected to.

10. Modern cars are stuffed with electronic devices. Give some examples of feedback control systems in cars.
    **A feedback control system uses the output of the system to modify the input.**
        - An example of such a system in cars is the **cruise control system**. This control system uses the output feedback to manage a constant speed which is done by calculating the acutal speed and compare that to the wanted speed. When any changes in speed happens (events), the system will adjust the throttle as necessary. 
        - Another example is the the **anti-locking braking system**, refered to as ABS. This system operates through the use of sensors that are located near each wheel to detect when it rotates very quickly. When this event happens, the system will apply and release the brakes really quick which in return will let the driver get control over the car. 
        - Another example is **lane keeping assist**, refered to as LKA. The system works by monitoring the car position with respect to the boundry of the lane. If an event of lane departure is about to happen then the system applies torque to the steering wheel, as well as pressure to the brakes to catch the attention of the driver. 
        - Another example is the **automatic emergency braking**, refered to as AEB. The way this control system works is by detecting possible accidents with the objects in the path of the car. It relies on sensors, cameras, and radars. Once an event is about to occure of a potential collision, the system automatically brakes to avoid such events or at least lessen the impact of them. 