# 📚 Curated System Design Bibliography & Whitepapers

The best distributed systems engineers don't learn from random blog spam—they learn from seminal academic papers, canonical textbooks, and production engineering incident write-ups.

---

## 📖 Essential Textbooks

1. **"Designing Data-Intensive Applications (DDIA)" by Martin Kleppmann**
   - *The undisputed bible of modern distributed systems.*
   - **Key Chapters to Focus On**:
     - Chapter 3: Storage and Retrieval (SSTables, LSM-Trees, B-Trees)
     - Chapter 5: Replication (Leader-Follower, Split-brain, Quorums)
     - Chapter 6: Partitioning (Sharding, Rebalancing)
     - Chapter 7: Transactions (ACID, Isolation levels, SSI)
     - Chapter 8: The Trouble with Distributed Systems (Unreliable networks, clocks, byzantine faults)
     - Chapter 9: Consistency and Consensus (Linearizability, Raft, Paxos, 2PC)

2. **"System Design Interview – An Insider's Guide" (Volumes 1 & 2) by Alex Xu & Sahn Lam**
   - *Best tactical interview preparation guide with crisp visual diagrams.*
   - Covers Rate Limiter, Consistent Hashing, Key-Value Store, Unique ID Generator, YouTube, Google Drive, Payment Systems, Digital Wallet, Proximity Service.

3. **"Database Internals: A Deep Dive into How Distributed Data Systems Work" by Alex Petrov**
   - *The definitive guide to storage engines, B-Tree variants, distributed coordination, and consensus.*

4. **"Site Reliability Engineering: How Google Runs Production Systems" by Betsy Beyer et al.**
   - *Practical lessons from Google on SLOs, SLAs, SLIs, error budgets, handling overload, and cascading failure prevention.*

---

## 📜 Landmark Whitepapers Every Architect Should Read

| Paper | Authors / Organization | Why It Changed the Industry |
|---|---|---|
| **[The Google File System (GFS)](https://research.google/pubs/the-google-file-system/)** | Sanjay Ghemawat, Howard Gobioff, Shun-Tak Leung (2003) | Showed that commodity, failing hardware can host distributed file storage via chunking and master-chunk architecture. |
| **[MapReduce: Simplified Data Processing on Large Clusters](https://research.google/pubs/mapreduce-simplified-data-processing-on-large-clusters/)** | Jeffrey Dean, Sanjay Ghemawat (2004) | Created the modern big-data era and inspired Apache Hadoop. |
| **[Bigtable: A Distributed Storage System for Structured Data](https://research.google/pubs/bigtable-a-distributed-storage-system-for-structured-data/)** | Chang et al., Google (2006) | Defined sparse, distributed, persistent multi-dimensional sorted maps. Inspired Apache HBase and Cassandra. |
| **[Dynamo: Amazon’s Highly Available Key-value Store](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)** | DeCandia et al., Amazon (2007) | Introduced Consistent Hashing, Vector Clocks, Sloppy Quorums, and Hinted Handoff for ultimate availability ($99.999\%$). |
| **[In Search of an Understandable Consensus Algorithm (Raft)](https://raft.github.io/raft.pdf)** | Diego Ongaro & John Ousterhout, Stanford (2014) | Replaced the notoriously unintuitive Paxos with a clean, understandable consensus protocol for leader election and state machine replication. |
| **[Spanner: Google’s Globally-Distributed Database](https://research.google/pubs/spanner-googles-globally-distributed-database/)** | Corbett et al., Google (2012) | Brought externally consistent distributed transactions worldwide using atomic clocks and GPS receivers (TrueTime API). |
| **[Kafka: a Distributed Messaging System for Log Processing](https://www.microsoft.com/en-us/research/publication/kafka-a-distributed-messaging-system-for-log-processing/)** | Jay Kreps et al., LinkedIn (2011) | Reimagined message queues as distributed, partitioned, commit-log stream processors. |

---

## 🏢 Top Engineering Blogs for Real-World Case Studies

- **[Netflix Technology Blog](https://netflixtechblog.com/)**: Chaos Engineering, Zuul API gateway, microservice resilience, video encoding pipelines.
- **[Uber Engineering Blog](https://www.uber.com/blog/engineering/)**: Real-time geospatial dispatch (H3 hex indexing), ringpop, Schemaless, microservice observability.
- **[Discord Engineering Blog](https://discord.com/blog/engineering)**: Why Discord migrated from Go to Rust, how Discord stores billions of messages in ScyllaDB.
- **[Cloudflare Blog](https://blog.cloudflare.com/)**: Anycast routing, DDoS mitigation, HTTP/3 QUIC deep dives, edge computing.
- **[Meta Engineering](https://engineering.fb.com/)**: TAO (distributed graph store for social graph), Memcached scaling at billion-user scale, RocksDB.
