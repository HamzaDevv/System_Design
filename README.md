# 🏆 Practical System Design: Zero to Hero & Interactive Lab

> **A first-principles curriculum for mastering distributed systems, modern AI infrastructure, and system design interviews—with co-located theory guides, origin stories, revision checklists, and ByteByteGo-style interactive browser simulations.**

[![Curriculum](https://img.shields.io/badge/Curriculum-11%20Modules%20%E2%80%A2%2058%20Topics%20%E2%80%A2%2017%20Case%20Studies-7c3aed)](#%EF%B8%8F-master-curriculum-roadmap)
[![Interactive Labs](https://img.shields.io/badge/Interactive%20Labs-ByteByteGo%20SVG%20Simulators-059669)](#-how-to-run-the-interactive-simulations)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/HamzaDevv/System_Design)
[![Repo](https://img.shields.io/badge/GitHub-HamzaDevv%2FSystem__Design-181717?logo=github)](https://github.com/HamzaDevv/System_Design)

---

## 📖 Welcome to the Journey

Most system design resources either dump academic definitions without intuition or draw high-level boxes without showing *what physically breaks at scale*.

This repository follows a **"Discoverer" First-Principles Methodology** where **everything for a topic lives together in one folder** (`README.md` + `assets/` + `simulation.html`):

1. **Origin Story & History ("Why It Came")**: How real-world bottlenecks forced engineers to invent each layer and protocol.
2. **Deep First-Principles Notes (`<module>/<topic>/README.md`)**: Conceptual breakdowns, AI architectural visuals, trade-offs, capacity math, RFC references, and a **Revision To-Do & Suggested Reading Checklist**.
3. **ByteByteGo-Style Interactive Labs (`<module>/<topic>/simulation.html`)**: Self-contained, zero-dependency web visualisers built with Retina-sharp inline SVG, smooth delta-time animations, live wire traces, and side-by-side mode comparisons.

---

## 🗺️ Master Curriculum Roadmap (`Final v1.1`)

```text
[00. Foundations, Networking & Mental Models]
                      │
                      ▼
[01. Scalability, Proxies, Compute & Load Balancing]
                      │
                      ▼
[02. Caching Architectures & Edge Delivery]
                      │
                      ▼
[03. Storage Systems, Databases & Indexing]
                      │
                      ▼
[04. Asynchronous Processing, Queues & Event Streams]
                      │
                      ▼
[05. Reliability, Resiliency & Fault Tolerance]
                      │
                      ▼
[06. Distributed Consensus, Coordination & Time]
                      │
                      ▼
[07. Search, Real-Time, Geospatial & Data Pipelines]
                      │
                      ▼
[08. Security, Observability & Production Engineering]
                      │
                      ▼
[09. Modern AI & ML Infrastructure System Design]
                      │
                      ▼
[10. 17 End-to-End System Design Case Studies]
```

---

### Detailed Module Index & Progress Tracker

| Module | Core Topics Covered | Interactive Visual Lab | Status |
|---|---|---|:---:|
| **[00. Foundations & Networking](00-foundations/)** | Request-Response Lifecycle (DNS, TCP/UDP, IPv4/IPv6, OSI, TLS 1.3, HTTP), HTTP/1.1 vs HTTP/2 vs HTTP/3 QUIC, REST vs gRPC vs GraphQL + Webhooks, WebSockets/SSE/WebRTC, Latency/Availability Nines & FinOps Math, Serialization & Compression | [Packet Lifecycle](00-foundations/01-request-response-lifecycle/simulation.html) • [Protocol Evolution](00-foundations/02-protocol-evolution/simulation.html) | 🟢 Active (`2/6`) |
| **[01. Scalability, Compute & LB](01-scalability-load-balancing/)** | Horizontal vs Vertical Scaling & Scale Cube, Reverse Proxies & API Gateways, L4 vs L7 Load Balancing & GeoDNS/GSLB, LB Algorithms, Consistent Hashing & Virtual Nodes, Service Discovery, Monolith vs Microservices & Service Mesh (Envoy), Containers/MicroVMs & C10K `epoll` I/O | [Load Balancer Simulator](01-scalability-load-balancing/04-load-balancing-algorithms/simulation.html) | 🟡 Lab Live (`0/8`) |
| **[02. Caching & Edge Delivery](02-caching-and-cdn/)** | Cache-Aside / Write-Through / Write-Behind, Eviction (LRU, LFU, W-TinyLFU, ARC), Penetration / Hot-Key Breakdown / Stampede, Redis Internals & Cluster, CDNs & Anycast | [Simulation Hub](index.html) *(Planned)* | ⚪ Planned |
| **[03. Storage Systems & Databases](03-database-storage-systems/)** | SQL vs NoSQL + Normalization/Denormalization, MVCC, Isolation & Linearizability, CAP & PACELC, Replication Lag & CRDTs, Sharding & Federation, B+Trees vs LSM-Trees & Indexing, 2PC / Outbox / Sagas, Block/File/Object Storage (Pre-Signed URLs) & Columnar OLAP/Lakehouse | [Simulation Hub](index.html) *(Planned)* | ⚪ Planned |
| **[04. Async Processing & Streams](04-asynchronous-messaging/)** | Queues vs Event Logs, Kafka Internals (Partitions, Offsets, Zero-Copy, ISR), Delivery Guarantees & Idempotency, Event Sourcing, CQRS & CDC, Distributed Job Scheduling | [Simulation Hub](index.html) *(Planned)* | ⚪ Planned |
| **[05. Reliability & Fault Tolerance](05-resilience-fault-tolerance/)** | Grey & Cascading Failures, Rate Limiting (Token/Leaky Bucket, Sliding Window), Circuit Breakers, Backoff & Full Jitter, Bulkheads & Load Shedding, Multi-Region Active-Active & RPO/RTO | [Simulation Hub](index.html) *(Planned)* | ⚪ Planned |
| **[06. Consensus, Coordination & Time](06-distributed-consensus-coordination/)** | Two Generals & FLP Impossibility, Raft & Paxos, Distributed Locking & Fencing Tokens (etcd/ZooKeeper), Gossip & SWIM, Snowflake / UUIDv7, Lamport, Vector Clocks & TrueTime | [Simulation Hub](index.html) *(Planned)* | ⚪ Planned |
| **[07. Search, Real-Time & Geospatial](07-search-realtime-geospatial/)** | Full-Text Inverted Indexes & BM25, 1M+ Concurrent WebSockets & Presence, Geospatial Indexing (Geohash, Quadtree, S2, H3) & Proximity/Maps, Batch/Stream ETL, MapReduce/Spark Shuffle, Windowing & Top-K Heavy Hitters | [Simulation Hub](index.html) *(Planned)* | ⚪ Planned |
| **[08. Security, Observability & Prod](08-security-observability-production/)** | AuthN/AuthZ (Sessions, JWT, OAuth2/OIDC, RBAC), mTLS, KMS & DDoS Defence, Logging/Metrics/Tracing (OpenTelemetry & p99), SLIs/SLOs/Error Budgets, Zero-Downtime Deployments, Expand-Contract Migrations & 9 Types of API Testing | [Simulation Hub](index.html) *(Planned)* | ⚪ Planned |
| **[09. Modern AI & ML Infrastructure](09-ai-ml-systems/)** | Vector Search (HNSW, IVF-PQ) & Hybrid Retrieval, LLM Serving (Prefill/Decode, KV Cache, PagedAttention, Continuous Batching), AI Gateways & Semantic Caching, Recommendation Pipelines, Distributed ML Training & Agentic AI Systems | [Simulation Hub](index.html) *(Planned)* | ⚪ Planned |
| **[10. End-to-End Case Studies](10-case-studies/)** | 17 Full Blueprints: TinyURL, Rate Limiter, Autocomplete/Crawler, Notifications, WhatsApp Chat, Newsfeed, Dropbox, YouTube/Netflix, Ticketmaster, Uber/Maps, Stripe/UPI Ledger, Google Docs, Datadog, Ad Aggregator/Leaderboard, Enterprise RAG, Dynamo KV Store, Job Scheduler | End-to-End Architecture Blueprints | ⚪ Planned |

<details>
<summary><strong>📌 View All 17 Module 10 Case Studies</strong></summary>

1. **TinyURL / URL Shortener & Pastebin** — Base62, KGS, read-heavy caching
2. **Distributed Rate Limiter Service** — Edge enforcement, Redis Lua atomicity
3. **Search Autocomplete & Distributed Web Crawler** — Prefix tries, politeness, URL frontier
4. **Multi-Channel Notification Engine** — Push/SMS/Email fan-out, priority queues, dedup
5. **Real-Time Chat System (WhatsApp / Slack)** — WebSocket routing, offline sync, group fan-out
6. **Social Media Newsfeed (X / Instagram)** — Hybrid fan-out on write vs read, celebrity hotspots
7. **Cloud File Storage & Sync (Dropbox / Google Drive)** — Block chunking, dedup, delta sync
8. **Video Streaming Platform (YouTube / Netflix)** — Transcoding DAG, HLS/DASH, Open Connect CDN
9. **Flash Sale & Ticket Booking (Ticketmaster / BookMyShow)** — Seat hold TTL, waiting rooms, locking
10. **Ride-Sharing & Proximity Dispatch (Uber / Ola / Yelp)** — Geospatial indexing, location streams, matching & ETA
11. **Payment Gateway & Double-Entry Ledger (Stripe / UPI)** — Strict idempotency, reconciliation
12. **Collaborative Document Editor (Google Docs)** — Operational Transformation vs CRDTs
13. **Distributed Metrics & Monitoring (Datadog / Prometheus)** — High-write TSDB, downsampling
14. **Ad Click Aggregator, Top-K Heavy Hitters & Gaming Leaderboard** — Stream windowing, Count-Min Sketch, Redis Sorted Sets
15. **Enterprise RAG & AI Copilot Platform** — Hybrid search, multi-tenant ACLs, streaming tokens
16. **Distributed Key-Value Store (Amazon Dynamo / Cassandra)** — Consistent hashing, sloppy quorums, Merkle trees, LSM
17. **Distributed Job & Workflow Scheduler (Cron / Temporal / Airflow)** — Partitioned time buckets, idempotent workers, leases & DAG state

</details>

---

## 📁 Unified Repository Work Tree

Every module and topic co-locates its **notes (`README.md`)**, **diagrams (`assets/`)**, and **interactive simulator (`simulation.html`)** side by side:

```text
System_Design/
├── README.md                                  # Master curriculum, roadmap, and project index
├── agent.md                                   # Learning state, syllabus lock, doc & lab specs
├── index.html                                 # Central Visual Lab Hub (GitHub Pages entry)
├── cheatsheets/                               # Quick-revision sheets for interviews
│   ├── latencies-numbers-every-programmer-should-know.md
│   ├── system-design-formulas-and-estimations.md
│   └── interview-framework-and-rubric.md
├── resources/                                 # Curated books, whitepapers, and engineering blogs
│   └── recommended-books-and-papers.md
├── 00-foundations/                            # Module 00: Foundations & Networking
│   ├── README.md
│   ├── 01-request-response-lifecycle/
│   │   ├── README.md                          # Origin Story, Deep Dive, Revision To-Do
│   │   ├── assets/request-response-lifecycle.jpg
│   │   └── simulation.html                    # ✅ Live: DNS → TCP → TLS 1.3 → HTTP/DB
│   └── 02-protocol-evolution/
│       ├── README.md                          # Origin Story, Deep Dive, Revision To-Do
│       ├── assets/http-protocol-evolution.jpg
│       └── simulation.html                    # ✅ Live: HTTP/1.1 vs HTTP/2 vs HTTP/3 QUIC
├── 01-scalability-load-balancing/             # Module 01: Scalability, Proxies & Load Balancing
│   ├── README.md
│   └── 04-load-balancing-algorithms/
│       └── simulation.html                    # ✅ Live: LB algorithms & traffic flow
├── 02-caching-and-cdn/                        # Module 02: Caching & Edge Delivery
│   └── README.md
├── 03-database-storage-systems/               # Module 03: Storage Systems & Databases
│   └── README.md
├── 04-asynchronous-messaging/                 # Module 04: Async Processing & Streams
│   └── README.md
├── 05-resilience-fault-tolerance/             # Module 05: Reliability & Fault Tolerance
│   └── README.md
├── 06-distributed-consensus-coordination/     # Module 06: Consensus, Coordination & Time
│   └── README.md
├── 07-search-realtime-geospatial/             # Module 07: Search, Real-Time & Geospatial
│   └── README.md
├── 08-security-observability-production/      # Module 08: Security, Observability & Prod
│   └── README.md
├── 09-ai-ml-systems/                          # Module 09: Modern AI & ML Infrastructure
│   └── README.md
└── 10-case-studies/                           # Module 10: 15 End-to-End Case Studies
    └── README.md
```

---

## ⚡ 4-Step System Design Interview Framework

Whenever tackling any design prompt (or working through **Module 10**), apply this structured 4-step loop:

```text
┌─────────────────────────────────────────────────────────────┐
│ Step 1: Understand Problem & Scope (3–5 min)                │
│  • Clarify functional requirements (core user actions)      │
│  • Clarify non-functional requirements (availability,       │
│    p99 latency, consistency model, throughput scale)        │
│  • Define explicit non-goals and system boundaries          │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│ Step 2: Back-of-the-Envelope Estimation (5 min)             │
│  • DAU, Read:Write ratio, average & peak QPS                │
│  • Daily and 5-year storage footprint                       │
│  • Ingress/Egress bandwidth & 80/20 hot-set cache memory    │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│ Step 3: High-Level Design (10–15 min)                       │
│  • API contracts (REST / gRPC / WebSockets)                 │
│  • Core data model, database choice, and primary keys       │
│  • End-to-end flow (Client → Edge → Service → Cache → DB)   │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│ Step 4: Deep Dive & Bottleneck Resolution (15–20 min)       │
│  • Eliminate Single Points of Failure (SPOFs)               │
│  • Sharding, replication lag, hot keys & async queues       │
│  • Resiliency (rate limits, circuit breakers, idempotency)  │
│  • Observability, security & CAP/PACELC trade-offs          │
└─────────────────────────────────────────────────────────────┘
```

---

## 🧪 How to Run the Interactive Simulations

Every simulation is a **100% self-contained single-file HTML/CSS/SVG/JS app**—zero build tools, zero npm installs, and works offline.

### Option 1: Direct File Open
Open the central hub [`index.html`](index.html) (or any topic's `simulation.html`) directly in your browser:
- **macOS**: `open index.html`
- **Linux**: `xdg-open index.html`
- **Windows**: `start index.html`

### Option 2: Local HTTP Server (Python)
From the repository root:
```bash
python3 -m http.server 8000
```
Then open [http://localhost:8000/](http://localhost:8000/) in your browser.

---

## 📚 Curated Bibliography & Top Resources

- **Books**:
  - *Designing Data-Intensive Applications (DDIA)* — Martin Kleppmann
  - *System Design Interview – An Insider's Guide (Vols. 1 & 2)* — Alex Xu & Sahn Lam
  - *Database Internals: A Deep Dive* — Alex Petrov
  - *Site Reliability Engineering (SRE)* — Google
- **Foundational Papers**:
  - Google File System (GFS), MapReduce, Bigtable, Spanner (TrueTime), Borg
  - Amazon Dynamo, Raft Consensus, Apache Kafka, Facebook Gorilla, vLLM / PagedAttention
- **Engineering Blogs**:
  - Netflix TechBlog, Uber Engineering, Meta Engineering, Discord Blog, Cloudflare Blog, Stripe Engineering

---

## 🤝 Contributing & Community

Contributions are welcome! If you spot a typo, want to sharpen a trade-off analysis, or add a new simulation following the whiteboard design spec in [`agent.md`](agent.md):
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-topic`)
3. Commit your changes (`git commit -m 'feat: add amazing simulation'`)
4. Push to the branch (`git push origin feature/amazing-topic`)
5. Open a Pull Request

---

*Curated with passion for engineers aiming to build planet-scale systems.* 🌍
