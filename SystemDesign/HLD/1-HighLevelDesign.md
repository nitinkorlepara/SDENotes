# High Level Design

- Decomposing requirements into differenct microservices
- Defining APIs and communication protocols between services
- Identifying data storage solutions and data flow
- Designing for scalability, reliability, and maintainability
- Creating architecture diagrams and documentation

- **Event Stroming** : explore complex business domains
  - Invite right people ( include domain and technical experts)
  - provide modeling space
  - Explore domain events
  - Look for aggregates (An aggregate is the portion of the system that receives commands and decides where to execute them or not)
  - emphasise on use of Ubiquitous language
  - Events
    - Domain Events
    - External System Events
    - USer Journey
    - Business Rules
    - Pain Points in the design
- Example of Order Processing in Retail Store
- ![EventStromingExample](/SystemDesign/HLD/Images/EventStromingExample.png)

- **Service Identification**
- Criteria
  - Rate of change
  - scalablity
  - LIfecycle management
  - isolated failure

# References

- [1 Event Stroming](https://www.lucidchart.com/blog/ddd-event-storming)
- [2 Event Stroming](https://ziobrando.blogspot.com/2013/11/introducing-event-storming.html#.VbhQTn-9KK1)
- [3 Event Stroming](https://sch3lp.github.io/2014/07/12/event-storming-exercise/)
