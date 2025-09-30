# Spring Data

### DTO (Data Transfer Objects)

- A DTO (Data Transfer Object) is a simple object whose main purpose is to carry data between processes, layers, or services in a system.
- DTOs can be optimizaed for JSON serialization and deserialization

### Application Properties

```
    #H2 in-memory database
    spring.datasource.url=jdbc:h2:mem:testdb
    spring.datasource.driverClassName=org.h2.Driver
    spring.datasource.username=sa
    spring.datasource.password=

    #H2 Console (web UI)
    spring.h2.console.enabled=true
    spring.h2.console.path=/h2-console

    #JPA / Hibernate settings
    spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
```

### hibernate

```
    @GeneratedValue(generator ="UUID")
    @GenericGenerator(name="UUID", stratetgy = "org.hibernate.id.UUIDGenerator")


    or a simple
    @UUIDGenerator
```

![hibernate DDL](/FrameWorks/HibernateDDL.png)
