**BASE**

- Basic Availability: The system is available most of the time.
- Soft State: The state of the system may change over time, even without new input.
- Eventual Consistency: The system will be available even in the presence of failures, ensuring that it can respond to requests.

**ACID**

- Atomicity: Transaction should be executed entirely or not at all.
- Consistency: Transaction should bring the database from one valid state to another valid state.
- Isolation: Concurrent execution of transactions should result in a system state that would be obtained if transactions were executed sequentially.
- Durability: Once a transaction has been committed, its effects will remain permanent even in the face of system failure or crashes.

### Additional Resources

- [ACID Properties Explained](https://www.geeksforgeeks.org/acid-properties-in-dbms/)
- [Understanding BASE vs ACID](https://www.digitalocean.com/community/tutorials/understanding-acid-and-base-in-databases)
- [No SQL](https://www.mongodb.com/resources/basics/databases/nosql-explained)
