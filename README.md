# 🚀 Practical System Design: Zero to Hero & Interactive Lab

> **A curated, first-principles curriculum for mastering distributed systems and system design interviews, paired with interactive browser-based visual simulations.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/HamzaDevv/System_Design)
[![Repo](https://img.shields.io/badge/GitHub-HamzaDevv%2FSystem__Design-181717?logo=github)](https://github.com/HamzaDevv/System_Design)

---

## 📖 Welcome to the Journey

Welcome to the definitive, battle-tested System Design repository. Most resources either give purely academic definitions with no intuition or provide high-level 2D boxes without explaining *why* things break at scale.

This project is built around a two-step learning methodology:
1. **Curated First-Principles Notes (`docs/`)**: Thorough conceptual breakdowns, architectural diagrams, edge cases, trade-offs, mathematical estimations, and failure modes.
2. **Interactive Visual Simulations (`interactive-simulations/`)**: Standalone web applications built with HTML5, CSS3, and modern JavaScript that bring algorithms (Load Balancing, Consistent Hashing, Cache Eviction, Rate Limiting, Circuit Breakers, Kafka Offsets) to life.

---

## 🗺️ Master Curriculum Roadmap

```
[Module 00: Foundations & Mental Models]
                 │
                 ▼
[Module 01: Scalability, Proxies & Load Balancing]
                 │
                 ▼
[Module 02: Caching Architectures & CDN]
                 │
                 ▼
[Module 03: Storage Systems, Databases & Indexing]
                 │
                 ▼
[Module 04: Asynchronous Processing & Event Streams]
                 │
                 ▼
[Module 05: Reliability, Resiliency & Fault Tolerance]
                 │
                 ▼
[Module 06: Distributed Consensus & Coordination]
                 │
                 ▼
[Module 07: Real-Time & Geospatial Architectures]
                 │
                 ▼
[Module 08: End-to-End Interview Case Studies]
```

---

### Detailed Module Index & Progress Tracker

| Module | Core Topics | Interactive Visual Lab | Status |
|---|---|---|:---:|
| **[00. Foundations & Networking](docs/00-foundations/)** | Request Lifecycle, OSI vs TCP/IP, HTTP/1.1 vs HTTP/2 vs HTTP/3, WebSockets, gRPC, Latency Numbers Every Engineer Must Know, Capacity Estimations | Network Packet Lifecycle Simulator | 🟡 In Progress |
| **[01. Scalability & Load Balancing](docs/01-scalability-load-balancing/)** | Horizontal vs Vertical, L4 vs L7 Load Balancing, Reverse Proxies, Consistent Hashing Ring, Virtual Nodes | [Load Balancer & Consistent Hash Ring](interactive-simulations/) | ⚪ Planned |
| **[02. Caching & Edge Computing](docs/02-caching-and-cdn/)** | Cache-Aside, Write-Through/Back, Eviction (LRU/LFU/ARC), Cache Stampede/Avalanche, Redis Internals, CDN & Anycast | [Cache Eviction & Stampede Playground](interactive-simulations/) | ⚪ Planned |
| **[03. Storage Systems & Databases](docs/03-database-storage-systems/)** | SQL vs NoSQL, ACID vs BASE, Replication Lag, Sharding Strategies, B+Trees vs LSM-Trees, Bloom Filters, 2PC & Sagas | [B+Tree vs LSM-Tree Visualizer](interactive-simulations/) | ⚪ Planned |
| **[04. Asynchronous Messaging](docs/04-asynchronous-messaging/)** | Message Queues vs Pub/Sub, Kafka Partitions, Consumer Rebalance, Idempotency, DLQ, Event Sourcing & CQRS | [Kafka Partition & Offset Stream](interactive-simulations/) | ⚪ Planned |
| **[05. Reliability & Fault Tolerance](docs/05-resilience-fault-tolerance/)** | Rate Limiting (Token/Leaky Bucket, Sliding Window), Circuit Breakers, Exponential Backoff & Full Jitter, Bulkheads, Multi-Region DR | [Rate Limiter Sandbox & Circuit Breaker](interactive-simulations/) | ⚪ Planned |
| **[06. Distributed Consensus](docs/06-distributed-consensus-coordination/)** | Two Generals' Problem, Raft Consensus (Leader Election & Log Replication), Distributed Locking (Redlock), Snowflake ID Generator, Clock Skew | [Raft Leader Election Simulator](interactive-simulations/) | ⚪ Planned |
| **[07. Real-Time & Geospatial](docs/07-realtime-geospatial/)** | WebSockets & SSE at 1M+ Concurrency, Presence Systems, Geospatial Indexing (Geohash, Quadtree, Google S2), Stream Windowing | [Geohash & Quadtree Visualizer](interactive-simulations/) | ⚪ Planned |
| **[08. Case Studies (Interviews)](docs/08-case-studies/)** | TinyURL, Notification Engine, WhatsApp Chat, Netflix Video Streaming, Twitter Newsfeed, Uber Ride Dispatch, Google Docs CRDT | System Architecture Blueprints | ⚪ Planned |

---

## 📁 Repository Directory Structure

```text
System_Design/
├── README.md                          # Master curriculum, roadmap, and project index
├── cheatsheets/                       # Fast reference sheets for interviews and quick review
│   ├── latencies-numbers-every-programmer-should-know.md
│   ├── system-design-formulas-and-estimations.md
│   └── interview-framework-and-rubric.md
├── docs/                              # Deep-dive theory notes and architectural blueprints
│   ├── 00-foundations/
│   ├── 01-scalability-load-balancing/
│   ├── 02-caching-and-cdn/
│   ├── 03-database-storage-systems/
│   ├── 04-asynchronous-messaging/
│   ├── 05-resilience-fault-tolerance/
│   ├── 06-distributed-consensus-coordination/
│   ├── 07-realtime-geospatial/
│   └── 08-case-studies/
├── interactive-simulations/           # Interactive HTML/CSS/JS visual simulations
│   ├── index.html                     # Central Visual Lab Launcher
│   ├── assets/                        # Shared styles, themes, and UI widgets
│   ├── 01-load-balancer-simulator/    # Round-Robin, Weighted, Least Conn, Consistent Hash
│   ├── 02-cache-eviction-visualizer/  # LRU, LFU, FIFO cache visualizer
│   ├── 03-rate-limiter-sandbox/       # Token Bucket, Leaky Bucket, Sliding Window
│   └── ...
└── resources/                         # Recommended books, whitepapers, and engineering blogs
    ├── recommended-books-and-papers.md
    └── engineering-blogs-and-links.md
```

---

## ⚡ 4-Step System Design Interview Framework

Whenever tackling any system design problem (or reading our case studies in Module 08), apply this standardized 4-step framework:

```
┌─────────────────────────────────────────────────────────────┐
│ Step 1: Understand Problem & Scope (3–5 min)                │
│  • Clarify functional requirements (core user actions)      │
│  • Clarify non-functional requirements (high availability,   │
│    low latency, consistency level, throughput scale)        │
│  • Define boundaries (what is explicitly OUT of scope)      │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│ Step 2: Back-of-the-Envelope Estimation (5 min)             │
│  • Daily Active Users (DAU), Read:Write Ratio               │
│  • Queries Per Second (QPS) — Average & Peak                │
│  • Storage estimations per day and over 5 years             │
│  • Bandwidth requirements (Ingress / Egress) & Memory Cache │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│ Step 3: High-Level Design (10–15 min)                       │
│  • API Design (REST/gRPC signatures)                        │
│  • Data Model (Database choice, schemas, primary keys)      │
│  • End-to-end component flow (Client -> Gateway -> Service  │
│    -> Cache -> Database -> Message Queue)                   │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│ Step 4: Deep Dive & Bottleneck Resolution (15–20 min)       │
│  • Identify single points of failure (SPOF)                 │
│  • Scaling bottlenecks (sharding, replication, partitioning)│
│  • Resiliency: Circuit breakers, rate limiters, fallback     │
│  • Trade-offs analysis (CAP/PACELC theorem considerations)  │
└─────────────────────────────────────────────────────────────┘
```

---

## 🧪 How to Run the Interactive Simulations

All simulations are pure client-side web apps (zero build tools required, no heavy npm install).

### Option 1: Direct File Open
Open `interactive-simulations/index.html` directly in your browser:
- On macOS: `open interactive-simulations/index.html`
- On Linux: `xdg-open interactive-simulations/index.html`
- On Windows: `start interactive-simulations/index.html`

### Option 2: Local HTTP Server (Python)
From the root of this repository:
```bash
python3 -m http.server 8000
```
Then visit [http://localhost:8000/interactive-simulations/](http://localhost:8000/interactive-simulations/) in your browser.

---

## 📚 Curated Bibliography & Top Resources

- **Books**:
  - *Designing Data-Intensive Applications (DDIA)* by Martin Kleppmann
  - *System Design Interview – An Insider's Guide (Volumes 1 & 2)* by Alex Xu & Sahn Lam
  - *Database Internals: A Deep Dive* by Alex Petrov
  - *Site Reliability Engineering (SRE)* by Google
- **Papers**:
  - Google File System (GFS), MapReduce, Bigtable, Spanner (TrueTime), Raft Consensus
  - Dynamo: Amazon's Highly Available Key-value Store
- **Tech Blogs**:
  - Netflix TechBlog, Uber Engineering, Meta Engineering, Discord Blog, Cloudflare Blog

---

## 🤝 Contributing & Community

Contributions are welcome! If you find a typo, want to improve an explanation, or contribute a new interactive simulation:
1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/amazing-topic`)
3. Commit your Changes (`git commit -m 'Add amazing simulation'`)
4. Push to the Branch (`git push origin feature/amazing-topic`)
5. Open a Pull Request

---

*Curated with passion for engineers aiming to build planet-scale systems.* 🌍
