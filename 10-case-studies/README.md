# 🏗️ Module 10: End-to-End System Design Case Studies

> [← Master Roadmap](../README.md) • [🏠 Simulation Hub](../index.html) • **Status: ⚪ Planned (`0/17`)**

Applying Modules `00` through `09` to 17 complete, production-grade architectures using our [4-Step System Design Interview Framework](../cheatsheets/interview-framework-and-rubric.md).

---

## 📂 Case Studies Index

| # | System | Core Architectural Challenges | Status |
|---|---|---|---|
| **10.1** | **TinyURL / URL Shortener & Pastebin** | Base62 encoding, Hashing vs Key Generation Service (KGS), Read-heavy caching | ⚪ Planned |
| **10.2** | **Distributed Rate Limiter Service** | Edge enforcement, Redis Lua atomicity, Fail-Open vs Fail-Closed | ⚪ Planned |
| **10.3** | **Search Autocomplete & Web Crawler** | Prefix Tries, Politeness, URL Frontier, Content Deduplication | ⚪ Planned |
| **10.4** | **Multi-Channel Notification Engine** | Push/SMS/Email fan-out, Priority queues, Deduplication & Retries | ⚪ Planned |
| **10.5** | **Real-Time Chat (WhatsApp / Slack)** | Stateful WebSocket routing, Offline sync, Group fan-out | ⚪ Planned |
| **10.6** | **Social Media Newsfeed (X / Instagram)** | Hybrid Fan-out on Write vs Read, Celebrity Hotspot mitigation | ⚪ Planned |
| **10.7** | **Cloud File Storage (Dropbox / Drive)** | Block chunking, Content-addressed deduplication, Delta sync | ⚪ Planned |
| **10.8** | **Video Streaming (YouTube / Netflix)** | Transcoding DAG, Adaptive Bitrate HLS/DASH, Open Connect CDN | ⚪ Planned |
| **10.9** | **Flash Sale & Ticket Booking** | Seat hold TTL, Optimistic/Distributed locks, Virtual waiting rooms | ⚪ Planned |
| **10.10** | **Ride-Sharing & Proximity Dispatch (Uber / Ola / Yelp)** | Geospatial indexing, Driver location streams, Matching & ETA | ⚪ Planned |
| **10.11** | **Payment Gateway & Double-Entry Ledger** | Strict idempotency, Exactly-once ledger, Async reconciliation | ⚪ Planned |
| **10.12** | **Collaborative Editor (Google Docs)** | Operational Transformation (OT) vs CRDTs, Cursor presence | ⚪ Planned |
| **10.13** | **Metrics & Log Monitoring (Datadog)** | High-write Time-Series DB, Downsampling, Streaming alerts | ⚪ Planned |
| **10.14** | **Ad Click Aggregator, Top-K Heavy Hitters & Leaderboard** | Stream windowing, Count-Min Sketch, Late-data reconciliation, Redis Sorted Sets | ⚪ Planned |
| **10.15** | **Enterprise RAG & AI Copilot Platform** | Hybrid search, Multi-tenant ACLs, Streaming tokens & Observability | ⚪ Planned |
| **10.16** | **Distributed Key-Value Store (Dynamo / Cassandra)** | Consistent hashing, Sloppy quorums, Hinted handoff, Merkle trees & LSM | ⚪ Planned |
| **10.17** | **Distributed Job & Workflow Scheduler (Cron / Temporal)** | Partitioned time buckets, Idempotent workers, Leases, DLQ & DAG state | ⚪ Planned |
