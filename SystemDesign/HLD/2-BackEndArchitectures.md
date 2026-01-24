# BackEnd Architectures

### Monolithic Architecture

- Monolithic pattern where the application created would have the UI and data access code in a single program.
- Single codebase and single build system.
- Deployment and testing are simple.
- Tightly coupled and poor reliability.
- Lack of flexibility.

### Microservice Architecture

- Allow organization to reduce dependencies, develop faster and scale.
- Microservices architecture enables the development of applications as a suite of small, independent services that can be deployed and scaled individually.
- This approach enhances flexibility and allows teams to adopt different technologies for different services, improving overall system resilience.
  - Saga Pattern
    - Orchestration (Centralised)
    - Choreography

### Service-Oriented Architecture

- Structured Apps into isolated, reusable services that communicate through common communication standards.
- service interface provide loose coupling between services
- Services are exposed using standard protocols such as SOAP,REST to exhange data.
  - ESB (Enterprise Service Bus) transformations of data models, handles connectivity, performs routing.

### References

- [Monolithic Architecture](https://www.techtarget.com/whatis/definition/monolithic-architecture#:~:text=A%20monolithic%20architecture%20is%20the,and%20unable%20to%20be%20changed.)
- [Service Oriented Architecture](https://www.ibm.com/think/topics/soa#:~:text=SOA%2C%20or%20service%2Doriented%20architecture,perform%20deep%20integration%20each%20time.)
- [microservices](https://microservices.io/)
- [1 SAGA](https://dzone.com/articles/microservices-using-saga-pattern)
- [2 SAGA](https://learn.microsoft.com/en-us/azure/architecture/patterns/saga)
