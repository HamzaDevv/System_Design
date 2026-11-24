# 🤖 System Design Teacher & Learning Agent State (`agent.md`)

> **Single Source of Truth for Learning Progress, Pedagogical Rules, Checkpoints, and Reference Architecture.**

---

## 🧭 Core Philosophy & Teaching Directives

### 1. The "Discoverer" First-Principles Rule
We do not treat system design as a trivia contest of buzzwords. We approach every problem as **discoverers**:
- **Start from the Physical Problem**: What physical boundary breaks? (CPU cache miss, mechanical disk seek, RAM saturation, network packet loss, speed of light across fiber cables).
- **Derive the Solution**: Why did engineers invent Load Balancers? Why did they invent LSM-Trees instead of B-Trees for heavy writes? Why did they invent Consistent Hashing?
- **Intuition Before Tool Names**: Understand the mathematical and physical mechanics before naming an open-source product (e.g., understand the commit log concept before naming Kafka).

### 2. The 4-Stage Learning Loop (Strictly Followed for Every Topic)
For every single topic in our roadmap, we execute this sequence:

```
[1. First-Principles Discussion] ──> [2. Deep Markdown Guide (docs/)]
                                                   │
                                                   ▼
[4. Git Commit & Checkpoint Update] <── [3. Interactive Web Lab]
```

1. **Step 1: First-Principles Discussion in Chat**
   - We walk through a discovery thought experiment together.
   - Ground the intuition: "What breaks when traffic scales by 100x?"
2. **Step 2: Deep-Dive Markdown Guide (`docs/...`)**
   - Comprehensive theoretical documentation to read, learn, and keep for the future.
   - Includes architectural diagrams (ASCII / Mermaid / Visual flowcharts), trade-off matrices, failure modes, and interview questions.
   - Grounded with external research, RFCs, and engineering blogs (Netflix, Meta, Uber, ByteByteGo, DDIA).
3. **Step 3: Interactive Visual Lab (`interactive-simulations/...`)**
   - HTML5/CSS3/JavaScript web simulation running 100% locally in the browser.
   - Live packet animations, interactive sliders, node failure injection, and metrics.
4. **Step 4: Checkpoint Update & Git Commit**
   - Mark the topic complete in `agent.md` and `README.md`.
   - Create a clean git commit so the repository stays up-to-date for your public GitHub.

---

## 📍 Current State & Checkpoint

| Field | Value |
|---|---|
| **Current Module** | `Module 00: Foundations, Network Protocols & Mental Models` |
| **Current Topic** | `01. The Request-Response Lifecycle: DNS, TCP Handshake, TLS 1.3 & HTTP` |
| **Stage** | `Stage 1: First-Principles Discovery & Deep-Dive Notes` |
| **Last Checkpoint Commit** | `51b61a2` (*Initial repository scaffold & Load Balancer Lab*) |

---

## 🗺️ Master Curriculum Checkpoint Tracker

### [Module 00: Foundations, Networking & Mental Models](docs/00-foundations/)
- [x] **00.1 The Request-Response Lifecycle** (DNS → TCP 3-Way Handshake → TLS 1.3 → HTTP request/response)
  - *Theory Notes*: [`docs/00-foundations/01-request-response-lifecycle.md`](docs/00-foundations/01-request-response-lifecycle.md)
  - *Interactive Lab*: [`interactive-simulations/00-packet-lifecycle-simulator/`](interactive-simulations/00-packet-lifecycle-simulator/)
- [ ] **00.2 Protocol Evolution** (HTTP/1.1 vs HTTP/2 Multiplexing vs HTTP/3 QUIC over UDP)
- [ ] **00.3 Communication Paradigms** (REST vs gRPC & Protobuf vs GraphQL)
- [ ] **00.4 Duplex & Streaming** (WebSockets vs Server-Sent Events vs Long Polling)
- [ ] **00.5 Physical Latency & Capacity Estimation** (Numbers every engineer must know, back-of-the-envelope math)

### [Module 01: Scalability, Proxies & Load Balancing](docs/01-scalability-load-balancing/)
- [ ] **01.1 Horizontal vs. Vertical Scaling & Stateless Architecture**
- [ ] **01.2 Reverse Proxies, Forward Proxies & API Gateways**
- [ ] **01.3 L4 (Transport) vs. L7 (Application) Load Balancing**
- [ ] **01.4 Load Balancing Algorithms** (Round Robin, Weighted, Least Connections, IP Hash)
- [ ] **01.5 Consistent Hashing Deep Dive** (Hash Ring, Virtual Nodes, Redistribution)
- [x] *Interactive Lab: Load Balancer & Traffic Simulator* (`interactive-simulations/01-load-balancer-simulator/`)

### [Module 02: Caching Architectures & Edge Delivery](docs/02-caching-and-cdn/)
- [ ] **02.1 Caching Topologies & Strategies** (Cache-Aside, Write-Through, Write-Behind, Write-Around)
- [ ] **02.2 Eviction Algorithms** (LRU, LFU, FIFO, ARC)
- [ ] **02.3 Cache Failure Pitfalls** (Cache Penetration, Cache Breakdown, Cache Avalanche, Stampede)
- [ ] **02.4 Distributed Caching & Redis Internals** (Single-threaded event loop, RDB/AOF, Sentinel/Cluster)
- [ ] **02.5 Content Delivery Networks (CDNs) & Anycast Routing**
- [ ] *Interactive Lab: Cache Eviction & Stampede Playground*

### [Module 03: Storage Systems, Databases & Indexing](docs/03-database-storage-systems/)
- [ ] **03.1 SQL vs NoSQL: The Fundamental Storage Paradigm**
- [ ] **03.2 ACID vs BASE & The CAP / PACELC Theorems**
- [ ] **03.3 Replication Topologies & Replication Lag** (Single-Leader, Multi-Leader, Leaderless Dynamo)
- [ ] **03.4 Sharding & Partitioning Strategies** (Range, Hash, Directory, Hotspots)
- [ ] **03.5 Storage Engine Internals** (B+Trees vs LSM-Trees, SSTables, Bloom Filters)
- [ ] **03.6 Distributed Transactions** (Two-Phase Commit vs Saga Pattern)
- [ ] *Interactive Lab: B+Tree vs LSM-Tree Storage Visualizer*

### [Module 04: Asynchronous Processing & Event Streams](docs/04-asynchronous-messaging/)
- [ ] **04.1 Synchronous vs Asynchronous Communication & Message Queues**
- [ ] **04.2 Apache Kafka Internals** (Partitions, Offsets, Consumer Groups, Rebalance)
- [ ] **04.3 Delivery Guarantees & Idempotency** (At-most-once, At-least-once, Exactly-once, DLQ)
- [ ] **04.4 Event Sourcing & CQRS**
- [ ] *Interactive Lab: Kafka Partition & Consumer Group Stream*

### [Module 05: Reliability, Resiliency & Fault Tolerance](docs/05-resilience-fault-tolerance/)
- [ ] **05.1 Failure Modes in Distributed Systems** (Cascading failures, slow dependencies)
- [ ] **05.2 Rate Limiting & Throttling Algorithms** (Token Bucket, Leaky Bucket, Sliding Window)
- [ ] **05.3 Circuit Breaker Pattern** (Closed $\rightarrow$ Open $\rightarrow$ Half-Open state machine)
- [ ] **05.4 Retries, Exponential Backoff & Full Jitter**
- [ ] **05.5 Bulkheads, Timeouts & Disaster Recovery (RPO / RTO)**
- [ ] *Interactive Lab: Rate Limiter Sandbox & Circuit Breaker Machine*

### [Module 06: Distributed Consensus & Coordination](docs/06-distributed-consensus-coordination/)
- [ ] **06.1 The Consensus Problem** (Two Generals' Problem, Byzantine Generals)
- [ ] **06.2 The Raft Consensus Algorithm** (Leader election, log replication, heartbeats)
- [ ] **06.3 Distributed Locking & Coordination** (Redlock vs ZooKeeper/etcd)
- [ ] **06.4 Distributed Unique ID Generation** (Twitter Snowflake, UUIDv7, ULID)
- [ ] **06.5 Time in Distributed Systems** (Clock skew, NTP, Vector Clocks, TrueTime)
- [ ] *Interactive Lab: Raft Consensus & Leader Election Playground*

### [Module 07: Real-Time & Geospatial Architectures](docs/07-realtime-geospatial/)
- [ ] **07.1 Real-Time Connections at Scale** (1M+ concurrent WebSockets, Presence systems)
- [ ] **07.2 Geospatial Indexing** (Geohash, Quadtree, Google S2 Geometry)
- [ ] **07.3 Stream Processing & Windowing** (Tumbling, Sliding, Session windows)
- [ ] *Interactive Lab: Geohash & Quadtree Visualizer*

### [Module 08: End-to-End System Design Case Studies](docs/08-case-studies/)
- [ ] **08.1 TinyURL / URL Shortener**
- [ ] **08.2 Distributed Rate Limiter Service**
- [ ] **08.3 Multi-Channel Notification Engine**
- [ ] **08.4 Real-Time Chat System (WhatsApp / Slack)**
- [ ] **08.5 Video Streaming Platform (YouTube / Netflix)**
- [ ] **08.6 Social Media Newsfeed (Twitter / Instagram)**
- [ ] **08.7 Flash Sale & Ticket Booking Engine (Ticketmaster)**
- [ ] **08.8 Ride-Sharing Dispatch System (Uber / Lyft)**
- [ ] **08.9 Real-Time Collaborative Document Editing (Google Docs - OT vs CRDT)**

---

## 📚 Internal Reference Library (`.references/` - Gitignored)

- `karanpratapsingh-system-design/`: Cloned from `https://github.com/karanpratapsingh/system-design` (architecture diagrams, module outlines, references).
- `bytebytego/explaining-9-types-of-api-testing.md`: Extracted guide on smoke, contract, stress, and security testing.
- Industry whitepapers (Dynamo, GFS, MapReduce, Bigtable, Raft, Kafka, Spanner).
