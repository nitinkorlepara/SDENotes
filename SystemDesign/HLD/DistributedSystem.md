# Distributed Systems

Distributing systems are used to solve problems.

- Computation
- Storage

#### Elements of a Distributed System

The most important functions of distributed computing are:

- **Resource sharing** - whether it’s the hardware, software or data that can be shared
- **Openness** - how open is the software designed to be developed and shared with each other
- **Concurrency** - multiple machines can process the same function at the same time
- **Scalability** - how do the computing and processing capabilities multiply when extended to many machines
- **Fault tolerance** - how easy and quickly can failures in parts of the system be detected and recovered
- **Transparency** - how much access does one node have to locate and communicate with other nodes in the system.

#### CAP

- **Consistency** - Giving correct result at any given time
- **Availability** - System should be available at all times
- **Partition tolerance** - even if one partition fails,system should be responsive

#### Architecture

- a cluster is defined as a group of nodes working together and configured in such a way that they appear as a single system.
  - Master Slave Architecture
  - Master Master Architecture

#### Cache

- temporary storage with high read speeds.
- Cache invalidation

  - Write through -> updated data is written to both database and ache at the same time
  - Write Around -> updated data is written to database first and then to cache
  - write back -> cache is updated first and then the database in specified time intervals

#### Scaling in Distributed System

- Vertical
  - Adding more resources to the existing server
  - ![Vertical Scaling](/SystemDesign/hld/Images/VerticalScaling.png)
- Horizontal
  - decentralising your server and adding more machines
  - ![Horizontal Scaling](/SystemDesign/hld/Images/HorizontalScaling.png)

#### Links

- [Types of Distributed Systems](https://www.confluent.io/learn/distributed-systems/)
- [Design Issues](https://www.geeksforgeeks.org/design-issues-of-distributed-system/)
- [Dimestions of System Scalability design](https://medium.com/@Pointnity_Network/three-dimensions-of-distributed-system-scalability-design-8e0319163c8d#:~:text=Scalability%20is%20an%20important%20indicator,two%20aspects%3A%20hardware%20and%20software)
- [CAP](https://mwhittaker.github.io/blog/an_illustrated_proof_of_the_cap_theorem/)
- [SOA](https://www.ibm.com/think/topics/soa#:~:text=SOA%2C%20or%20service%2Doriented%20architecture,perform%20deep%20integration%20each%20time)
- [Microservices](https://microservices.io/)

- [Distributd System Architecture](https://www.tutorialspoint.com/software_architecture_design/distributed_architecture.htm)
