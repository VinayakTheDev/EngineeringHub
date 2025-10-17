> It is ability of the system to handle increased workload by adding resources.

## **Types of Scalability**

- ### Vertical
	  Adding more resources to single machine / server (CPU, RAM, Storage) to handle increased load.
- ###  Horizontal
	  Adding more Machines to handle increased load.
- ###  Diagonal
	  Combination of Vertical and Horizontal Scaling. Start with Vertical scaling and switch to horizontal scaling when vertical limit is reached.

## **Challenges of Scalable System**

- ### Performance
    As workload on System increases , maintaining optimal performance becomes crucial. You need to better the experience without experiencing the slowdowns.
- ### Data Consistency
    When scaling horizontally, dealing with multiple copies of data distributed across multiple servers can be challenging. Need for synchronizing data between the nodes and account for potential failure or network latency.
- ### Complexity
    Scaling adds to complexity as considering how components interact and distribute workload and handle failures gracefully is important.
- ### Cost
    Horizontal Scaling can be cost-effective but need to track cost by carefully planning and estimating the load.
- ### Security
    Ensure security measures are in place to secure sensitive data and maintain integrity of the system.

## **Scalability Techniques**

- ### Load Balancing
    - Hardware Load Balancing
    - Software Load Balancing
- ### Caching
    - Client-Side
    - Server-Side
    - CDNs
- ### Database Scaling
    - Read Replicas
    - Sharding
    - NoSQL Databases
- ### Microservice Architecture
- ### Auto-Scaling
- ### Asynchronous processing (Queueing System)
- ### Cloud Computing

## **Trade-offs in Scalability**

- Latency vs Through-put
- cost vs scalability
- Data Partitioning Trade-off

# Scalability Principles that guides effective implementation
- ### Embrace Modularity 
	- Scaling isolated component is easier, reduces complexity.
- ### Optimize for Latency 
	- ensure responsive and satisfying user experience. Can be achieved by caching, data compression, effecient data retreival technique.