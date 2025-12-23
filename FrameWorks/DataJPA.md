# Data JPA

### DTO (Data Transfer Objects)

- A DTO (Data Transfer Object) is a simple object whose main purpose is to carry data between processes, layers, or services in a system.
- DTOs can be optimizaed for JSON serialization and deserialization

### Entity Life Cycle

- The entity life cycle in JPA includes several states: 
    - **Transient**: The entity is not yet persisted.
    - **Managed**: The entity is currently in a persistence context.
    - **Detached**: The entity is no longer managed but still exists in the database.
    - **Removed**: The entity is marked for deletion from the database.



### Mapping in Java

- In Java, mapping refers to the process of associating Java objects with database tables.
- This is typically done using annotations in JPA (Java Persistence API) to define how the object fields correspond to the database columns.

- **One - One**

  - In a one-to-one relationship, one entity is associated with exactly one instance of another entity.
  - Example:

    ```java
    @Entity
    public class User {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;

        @OneToOne(mappedBy = "user", cascade = CascadeType.ALL)
        private Profile profile;
    }

    @Entity
    public class Profile {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;

        @OneToOne
        @JoinColumn(name = "user_id")
        private User user;
    }
    ```

- **One - Many**

  - In a one-to-many relationship, one entity can be associated with multiple instances of another entity.
  - Example:

    ```java
    @Entity
    public class Department {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;

        @OneToMany(mappedBy = "department", cascade = CascadeType.ALL)
        private List<Employee> employees;
    }

    @Entity
    public class Employee {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;

        @ManyToOne
        @JoinColumn(name = "department_id")
        private Department department;
    }
    ```

- **Many - One**

  - In a many-to-one relationship, multiple instances of one entity can be associated with a single instance of another entity.
  - Example:

    ```java
    @Entity
    public class Order {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;

        @ManyToOne
        @JoinColumn(name = "customer_id")
        private Customer customer;
    }

    @Entity
    public class Customer {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;

        @OneToMany(mappedBy = "customer")
        private List<Order> orders;
    }
    ```

- **Many - Many**

  - In a many-to-many relationship, multiple instances of one entity can be associated with multiple instances of another entity.
  - Example:

    ````java
    @Entity
    public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

            @ManyToMany
            @JoinTable(
                name = "student_course",
                joinColumns = @JoinColumn(name = "student_id"),
                inverseJoinColumns = @JoinColumn(name = "course_id")
            )
            private List<Course> courses;
        }

        @Entity
        public class Course {
            @Id
            @GeneratedValue(strategy = GenerationType.IDENTITY)
            private Long id;

            @ManyToMany(mappedBy = "courses")
            private List<Student> students;
        }
        ```

    Example of Fetch Types:
    ````

### Fetch Types

- **EAGER**: This fetch type retrieves the associated entities immediately when the parent entity is loaded. It can lead to performance issues if not used carefully, as it may load a large amount of data.

  ```java
  @OneToMany(fetch = FetchType.EAGER)
  private List<Order> orders;
  ```

- **LAZY**: This fetch type retrieves the associated entities only when they are accessed for the first time. This is generally preferred for performance reasons, as it avoids loading unnecessary data.

  ```java
  @OneToMany(fetch = FetchType.LAZY)
  private List<Order> orders;
  ```

- **JOIN FETCH**: This is a JPQL (Java Persistence Query Language) feature that allows you to specify that associated entities should be fetched in the same query using a join.

  ```java
  SELECT p FROM Person p JOIN FETCH p.orders
  ```

- **SUBSELECT**: This fetch type retrieves associated entities using a subselect query. It can be useful for optimizing the retrieval of collections.

  ```java
  @OneToMany(fetch = FetchType.LAZY)
  @BatchSize(size = 10)
  private List<Order> orders;
  ```

### Application Properties

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

### hibernate

    @GeneratedValue(generator ="UUID")
    @GenericGenerator(name="UUID", stratetgy = "org.hibernate.id.UUIDGenerator")

    or a simple
    @UUIDGenerator

![hibernate DDL](/FrameWorks/HibernateDDL.png)
(hbm2ddl)
