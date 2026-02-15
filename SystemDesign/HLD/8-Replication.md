# Replication

**Replication** is to keep a copy of data on multiple machines.
- Each node that stores a copy of the database is a replica.
- Types
    - Leader Based Replication
    - Multi Leader Replication
    - LeaderLess Replication

## Leader-Based-Replication
A **Leader-Based Replica** has a master (leader) and slaves (followers):
- The leader receives all writes and sends changes to replicas.
- Replicas apply changes in the same order to maintain consistency.

### Types of Replication
- **Synchronous Replication**: The leader waits for replica acknowledgment before confirming a write.
- **Asynchronous Replication**: The leader doesn't wait, which is faster but risks data loss if the leader fails.

### Setting Up New Followers
1. Take a snapshot of the leader's data.
2. Copy the snapshot to the new follower node.
3. The follower connects to the leader and applies all changes from the backlog.
4. The follower catches up with the leader.

### High Availability with Leader-Based Replication
To ensure high availability in a leader-based replication system, several mechanisms are employed:

### Log Files
These are crucial for maintaining consistency and recovering from failures. Different types of log files include:
- **Statement-Based Replication**: Logs the SQL statements that modify the database. For example, if a user executes `INSERT INTO users (name) VALUES ('Alice');`, this statement is recorded in the log.
- **Write Ahead Log (WAL) Shipping**: Changes are written to a log before they are applied to the database, ensuring that in case of a failure, the system can replay the log to recover the state.
- **Logical (Row-Based) Log Replication**: Logs the actual changes made to the data at the row level. For instance, if a row is updated, the log will contain the old and new values of that row.
- **Trigger-Based Replication**: Uses database triggers to automatically replicate changes to other nodes. For example, when a new record is inserted into a table, a trigger can be set to automatically insert the same record into a replica.

### Leader Failure Handling
If the leader fails, one of the followers must be promoted to become the new leader. This process typically involves:
1. Electing a new leader from the available followers based on a consensus algorithm (e.g., Raft or Paxos).
2. Ensuring that the new leader has the most up-to-date data to minimize data loss.

By implementing these strategies, a leader-based replication system can achieve high availability and resilience against failures.

### Reading your own writes
**Reading Your Own Writes** (Read-Your-Write Consistency) ensures that after a client writes data, subsequent reads from that client will see the written data. This is important for user experience—users expect to see changes they just made immediately.

Implementation strategies:
- **Read from leader**: Route user's own writes and subsequent reads to the leader.
- **Track write timestamp**: Client tracks the timestamp of its last write; route reads to replicas with data at least as recent as that timestamp.
- **Version vectors**: Use versioning to ensure read consistency with user's own writes.

**Read-After-Write Consistency** guarantees that once data is written, all subsequent reads reflect that write. This prevents users from seeing stale data after making changes, improving data coherence in the application layer.

## Multi-Leader Replication

**Multi-Leader Replication** allows more than one node to accept writes, enabling distributed write operations across multiple leaders.

### Advantages
- **Clients with offline operation**: Allows clients to continue writing locally when disconnected; changes sync when reconnected.
- **Lower latency**: Writes can be processed locally without waiting for a remote leader.
- **Fault tolerance**: System remains operational even if one leader fails.

### Handling Write Conflicts
When multiple leaders accept writes simultaneously, conflicts can occur:
- **Last-write-wins (LWW)**: The write with the latest timestamp overwrites others (may lose data).
- **Custom resolution logic**: Application-specific rules determine which write takes precedence.
- **Convergent data types (CRDTs)**: Use data structures that automatically merge conflicting writes consistently.
- **Prompting users**: Alert users to conflicts and let them manually resolve them.

### Multi region replication topologies
Multi-region replication topologies define how data is replicated across geographically distributed leaders:

- **Circular topology**: Each region's leader replicates to the next region in a circular pattern. Simple but vulnerable to single node failures breaking the chain.
- **Star topology**: One central leader replicates to multiple regional leaders. Centralized control but creates a bottleneck at the center.
- **Mesh topology**: Every leader replicates to every other leader. Provides redundancy and fault tolerance but increases complexity and network overhead.

## Leaderless Replication

**Leaderless Replication** allows any replica to accept reads and writes, eliminating the need for a designated leader.

### Read Repair
- When a client reads from multiple replicas and detects stale data, it sends the latest value back to replicas with outdated information.
- Repairs inconsistencies lazily during read operations.

### Anti-Entropy Process
- Background process that continuously compares replicas and copies missing data between them.
- Ensures eventual consistency even if read repair doesn't catch all inconsistencies.
- Uses Merkle trees to efficiently identify differences.

### Quorum Consistency
- Reads and writes require acknowledgment from a quorum (majority) of replicas.
- If `w` (write quorum) + `r` (read quorum) > `n` (total replicas), strong consistency is guaranteed.
- Common configuration: `n=3`, `w=2`, `r=2`.

### Concurrent Writes
- Multiple replicas may receive writes simultaneously, creating conflicts.
- Resolved using last-write-wins, vector clocks, or application logic.

### Version Vectors
- Track causal relationships between writes across replicas.
- Each replica maintains a vector of logical timestamps for every other replica.
- Detects concurrent writes and partial ordering of events.

### Additional Considerations
- **Hinted handoff**: Temporarily store writes for unavailable replicas; deliver when they recover.
- **Read-your-write consistency**: Requires tracking client write timestamps or using sticky sessions.

