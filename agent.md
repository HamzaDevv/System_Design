# 🤖 System Design Teacher & Learning Agent State (`agent.md`)

> **Single Source of Truth for Learning Progress, Pedagogical Rules, Checkpoints, Locked Final Syllabus, Interactive Lab Design System, and Reference Architecture.**

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
[1. First-Principles Discussion] ──> [2. Deep Markdown Guide with AI Visuals (docs/)]
                                                   │
                                                   ▼
[4. Git Commit & Checkpoint Update] <── [3. ByteByteGo-Style Interactive Lab]
```

1. **Step 1: First-Principles Discussion in Chat**
   - We walk through a discovery thought experiment together.
   - Ground the intuition: "What physical constraint breaks when we scale?"
2. **Step 2: Deep-Dive Markdown Guide (`docs/...`)**
   - Comprehensive theoretical documentation to read, learn, and keep for the future.
   - **AI-Generated Architectural Visuals & Infographics**: Include high-clarity technical diagrams and AI-generated conceptual illustrations (`docs/assets/images/...`) wherever visual models reinforce intuition.
   - Grounded with external research, RFCs, and engineering blogs (Netflix, Meta, Uber, ByteByteGo, DDIA).
3. **Step 3: ByteByteGo-Style Interactive Lab (`interactive-simulations/...`)**
   - Clean, decluttered, Retina-sharp web simulation running 100% locally with zero external dependencies.
   - Must strictly follow the **Interactive Simulation Design System & Engineering Spec** below (using `interactive-simulations/00-packet-lifecycle-simulator/index.html` as the canonical gold-standard reference).
4. **Step 4: Checkpoint Update & Git Commit**
   - Mark the topic complete in `agent.md` and `README.md`.
   - Create a clean git commit so the repository stays up-to-date for your public GitHub.

### 3. Syllabus Lock Rule (`LOCKED — FINAL v1.0`)
- The **Master Curriculum** below (Modules `00` through `10`) is **fixed and final**.
- Do **not** add, remove, split, merge, or reorder modules or topics unless the user explicitly instructs to amend the lock.
- Progress only updates checkboxes (`[ ]` → `[x]`), file links, and the **Current State & Checkpoint** table.

---

## 🎨 Interactive Simulation Design System & Engineering Spec (Mandatory)

All future interactive labs under `interactive-simulations/` **MUST** adhere to this exact visual language, layout architecture, and animation engine. Do **not** generate dark neon/cyberpunk canvas themes unless explicitly requested.

### 1. Visual Theme: ByteByteGo Architectural Whiteboard (Light Mode)
- **Canvas & Surfaces**:
  - Page background: `#f4f6f9` (`--bg-page`)
  - Elevated cards/panels: `#ffffff` (`--bg-surface`) with `1px solid #e2e8f0` borders and subtle elevation (`0 4px 12px rgba(15, 23, 42, 0.06)`).
  - Diagram viewport: `#fcfdff` with a subtle architectural dot-grid (`radial-gradient(#d8e0eb 1.1px, transparent 1.1px)` at `20px × 20px`).
- **Semantic Protocol / Phase Palette**:
  - **Primary Ink**: `#0f172a` (headings), `#475569` (body), `#64748b` (metadata/labels)
  - **Purple (Discovery / Routing / DNS / Metadata)**: `#7c3aed` (tint `#f5f3ff`, border `#c4b5fd`)
  - **Amber (Transport / Handshake / Queuing / Backoff)**: `#d97706` (tint `#fffbeb`, border `#fcd34d`)
  - **Sky Blue (Security / Transit / Consensus / Network)**: `#0284c7` (tint `#f0f9ff`, border `#7dd3fc`)
  - **Emerald (Success / Application Flow / Healthy State)**: `#059669` (tint `#ecfdf5`, border `#6ee7b7`)
  - **Rose (Storage / DB Write / Bottleneck / Failure / Fault)**: `#e11d48` (tint `#fff1f2`, border `#fda4af`)
- **Typography**:
  - UI & Diagram Titles: `"Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`
  - Technical Values, IPs, Latencies, Logs & Packet Pills: `"JetBrains Mono", ui-monospace, SFMono-Regular, Menlo, monospace`

### 2. Diagram Rendering & Vector Architecture
- **Inline SVG Over HTML5 Canvas**: Build the topology using crisp, Retina-sharp inline `<svg viewBox="...">` so diagrams never blur on HiDPI/Retina displays and scale cleanly across viewports.
- **Architectural Zone Containers**: Group logical tiers inside soft-tinted dashed `<rect rx="14" stroke-dasharray="6 5">` zone boxes with uppercase micro-labels (e.g., *Client Network*, *DNS Hierarchy*, *Internet Backbone*, *Origin Datacenter*, *Storage Engine*).
- **Node Cards (No Hollow Neon Circles / No Raw Emoji Icons)**:
  - Represent every component (Client, LB, Cache, Broker, DB, Shard, Router) as a clean white rounded card (`rx="11"`, `stroke: #cbd5e1`, subtle drop-shadow) containing a tinted icon tile (`36×36px`) with a crisp custom inline SVG stroke icon, bold title, and monospace subtitle.
  - On active transit, highlight both the active source and destination cards with the phase accent colour and a gentle CSS pulse ring.
- **Connectors & State Overlays**:
  - Use smooth straight segments and cubic Bézier curves (`<path>`) with subtle directional markers.
  - When a persistent state changes (e.g., TLS tunnel established, Circuit Breaker opens, Leader elected, Cache warmed), visually transform the relevant path or badge on the diagram itself (e.g., emerald encrypted tunnel sheath + status pill).

### 3. Animation Engine & Physics Rules (Strict)
- **Path-Following Motion**: Animate packets/messages/tokens strictly along the actual SVG wire geometry using `pathEl.getPointAtLength(distance)`—never teleport across nodes or skip intermediate routers/hops.
- **Delta-Time Frame Loop**: Drive animations with `requestAnimationFrame` + `performance.now()` delta-time (`dt`) and smooth sine ease-in-out (`-(Math.cos(Math.PI * t) - 1) / 2`) so playback speed is identical on 60Hz and 120Hz+ displays.
- **Async Cancellation Token Pattern (Never Blind `setInterval`)**:
  - Chain multi-hop sequences with `async/await` and a monotonically incrementing `runToken`.
  - Auto-Play must await completion of each stage before pausing briefly (`~800ms`) and starting the next stage.
  - Reset, Mode Switch, or Direct Stage Jump must increment `runToken` to immediately and cleanly cancel any in-flight packet animation without ghost callbacks.
- **True Mid-Flight Pause / Resume**: Pausing freezes `elapsed` accumulation in the `requestAnimationFrame` loop so packets halt cleanly in place and resume without jumping.
- **Clamped Floating Packet Pills**: Attach a high-contrast monospace pill above each moving packet dot and clamp its `x`/`y` offset inside the SVG `viewBox` so labels never clip off screen edges.

### 4. Standard Page Layout & Pedagogical Components
Every simulation `index.html` must include these 5 clean vertical bands:
1. **Sticky Header**: Vector icon badge, topic title + flow subtitle, context pill (e.g., domain/endpoint/cluster spec), and `← Simulation Hub` back link (`../index.html`).
2. **Interactive Stage Stepper**: Clickable phase cards showing stage number (turning to `✓` when complete), subtitle, and estimated cost/latency badge. Clicking any stage jumps cleanly to it while pre-populating prior stage metrics accurately.
3. **Architecture Whiteboard Card**:
   - Top status bar with live pulsing status dot, plain-English step narration, and monospace HUD metric chips (e.g., `Hops`, `RTTs`, `Latency` or `Hit Rate`, `Throughput`, `Queue Depth`).
   - Dot-grid SVG diagram viewport with horizontal scroll fallback on small screens.
4. **Controls Toolbar**:
   - Left: Primary `▶ Next Stage` (switches to `↻ Replay` on completion), `⚡ Auto-Play All`, `⏸ Pause / ▶ Resume`, `↺ Reset`.
   - Right: Segmented pill toggles for **Speed** (`0.6× Slow` / `1× Normal` / `2× Fast`, defaulting to Slow for clarity) and **Comparison Mode** (e.g., `Cold Start` vs `Warm Keep-Alive`, `Cache-Aside` vs `Write-Through`, `Round Robin` vs `Least Connections`).
5. **Two-Column Bottom Educational Deck**:
   - **Left — First-Principles Insight Card**: Dynamic stage explanation with numbered takeaways, inline code tags, concept badges, and an end-of-run **Visual Summary Bar** (e.g., stacked latency/cost/distribution bar highlighting the core engineering takeaway).
   - **Right — Live Wire / Event Trace Table**: Scrollable monospace hop-by-hop log (`#`, `Phase`, `Hop/Component`, `Event/Frame`, `Δ Metric`) with subtle row-highlight flash and auto-scroll.

### 5. Runtime Constraints
- **100% Self-Contained**: Single `index.html` per lab (inline CSS + inline JS + inline SVGs). Zero external CDNs, zero external font dependencies required to render cleanly, zero build step—must open and run instantly via `file://` or GitHub Pages.
- **Canonical Reference File**: `interactive-simulations/00-packet-lifecycle-simulator/index.html`

---

## 📍 Current State & Checkpoint

| Field | Value |
|---|---|
| **Syllabus Status** | `LOCKED — Final v1.0 (11 Modules • 56 Core Topics • 15 Case Studies • 10 Interactive Labs)` |
| **Current Module** | `Module 00: Foundations, Networking & Mental Models` |
| **Current Topic** | `00.1 The Request-Response Lifecycle: DNS, TCP Handshake, TLS 1.3 & HTTP` |
| **Stage** | `Completed (Documentation + ByteByteGo-Style Whiteboard Simulation)` |
| **Next Topic** | `00.2 Protocol Evolution (HTTP/1.1 vs HTTP/2 Multiplexing vs HTTP/3 QUIC)` |
| **Last Checkpoint Commit** | `a1565d4` (*feat(simulator): refine packet lifecycle UI with clean controls, pause state, and segmented navigation*) |

---

## 🗺️ Master Curriculum Checkpoint Tracker (`FINAL v1.0 — LOCKED`)

### [Module 00: Foundations, Networking & Mental Models](docs/00-foundations/)
- [x] **00.1 The Request-Response Lifecycle** (DNS → TCP 3-Way Handshake → TLS 1.3 → HTTP request/response)
  - *Theory Notes*: [`docs/00-foundations/01-request-response-lifecycle.md`](docs/00-foundations/01-request-response-lifecycle.md)
  - *Interactive Lab*: [`interactive-simulations/00-packet-lifecycle-simulator/`](interactive-simulations/00-packet-lifecycle-simulator/)
- [ ] **00.2 Protocol Evolution** (HTTP/1.1 Head-of-Line Blocking vs HTTP/2 Multiplexing vs HTTP/3 QUIC over UDP)
- [ ] **00.3 Communication Paradigms** (REST vs gRPC & Protobuf vs GraphQL, Pagination & API Versioning)
- [ ] **00.4 Duplex & Real-Time Transport** (WebSockets vs Server-Sent Events vs Long Polling vs WebRTC)
- [ ] **00.5 Physical Latency, Throughput & Capacity Estimation** (Numbers every engineer must know, Little's Law, QPS/Storage/Bandwidth math)
- [ ] **00.6 Serialization, Compression & Checksums** (JSON, Protobuf, Avro, Thrift, gzip/zstd, Schema Evolution)

### [Module 01: Scalability, Proxies & Load Balancing](docs/01-scalability-load-balancing/)
- [ ] **01.1 Horizontal vs Vertical Scaling, Statelessness & Session Management**
- [ ] **01.2 Forward Proxies, Reverse Proxies, API Gateways & BFF Pattern**
- [ ] **01.3 L4 (Transport / DSR) vs L7 (Application) Load Balancing & TLS Termination**
- [ ] **01.4 Load Balancing Algorithms** (Round Robin, Weighted, Least Connections, Power of Two Choices, IP Hash)
- [ ] **01.5 Consistent Hashing Deep Dive** (Hash Ring, Virtual Nodes, Bounded Loads, Rebalancing)
- [ ] **01.6 Service Discovery, Health Checks & Client-Side vs Server-Side Load Balancing**
- [x] *Interactive Lab: Load Balancer & Traffic Simulator* (`interactive-simulations/01-load-balancer-simulator/`)

### [Module 02: Caching Architectures & Edge Delivery](docs/02-caching-and-cdn/)
- [ ] **02.1 Caching Layers & Topologies** (Cache-Aside, Read-Through, Write-Through, Write-Behind, Write-Around)
- [ ] **02.2 Eviction & Expiration Algorithms** (LRU, LFU, W-TinyLFU, FIFO, ARC, TTL Jitter)
- [ ] **02.3 Cache Failure Pitfalls & Defenses** (Penetration & Bloom Filters, Hot-Key Breakdown, Avalanche, Stampede & Singleflight)
- [ ] **02.4 Distributed Caching & Redis Internals** (Single-threaded I/O multiplexing, RDB/AOF, Sentinel, Redis Cluster Hash Slots)
- [ ] **02.5 Content Delivery Networks (CDNs), Origin Shielding, Edge Compute & Anycast Routing**
- [ ] *Interactive Lab: Cache Eviction & Stampede Playground* (`interactive-simulations/02-cache-eviction-simulator/`)

### [Module 03: Storage Systems, Databases & Indexing](docs/03-database-storage-systems/)
- [ ] **03.1 SQL vs NoSQL Data Models** (Relational, Key-Value, Document, Wide-Column, Graph, Time-Series)
- [ ] **03.2 Transactions, Isolation Levels & MVCC** (Read Committed, Snapshot Isolation, Serializable, Pessimistic vs Optimistic Locking)
- [ ] **03.3 ACID vs BASE & Distributed Trade-offs** (CAP Theorem & PACELC Framework)
- [ ] **03.4 Replication Topologies & Lag Anomalies** (Single-Leader, Multi-Leader, Leaderless Quorums $W+R>N$, Sloppy Quorums, Read-Your-Writes)
- [ ] **03.5 Partitioning & Sharding Strategies** (Range, Hash, Directory, Rebalancing, Celebrity Hotspots, Local vs Global Secondary Indexes)
- [ ] **03.6 Storage Engine Internals** (B+Trees vs LSM-Trees, WAL, MemTables, SSTables, Compaction, Bloom Filters, Connection Pooling)
- [ ] **03.7 Distributed Transactions** (Two-Phase Commit, Transactional Outbox Pattern, Saga Choreography vs Orchestration)
- [ ] **03.8 Blob/Object Storage, Distributed File Systems & Columnar OLAP** (S3, Chunking & Erasure Coding, Parquet, ClickHouse)
- [ ] *Interactive Lab: B+Tree vs LSM-Tree & Replication Quorum Visualizer* (`interactive-simulations/03-storage-engine-simulator/`)

### [Module 04: Asynchronous Processing, Queues & Event Streams](docs/04-asynchronous-messaging/)
- [ ] **04.1 Message Queues vs Event Logs** (Point-to-Point vs Pub/Sub, Push vs Pull, RabbitMQ/SQS vs Kafka)
- [ ] **04.2 Apache Kafka Internals** (Append-Only Log, Partitions, Offsets, Consumer Groups, Rebalance, Zero-Copy `sendfile`, ISR)
- [ ] **04.3 Delivery Guarantees, Idempotency Keys & Dead-Letter Queues** (At-Most-Once, At-Least-Once, Exactly-Once Semantics)
- [ ] **04.4 Event Sourcing, CQRS & Change Data Capture (CDC / Debezium)**
- [ ] **04.5 Distributed Task Queues, Delayed Job Scheduling & Workflow Orchestration** (Cron at Scale, Temporal, Backpressure)
- [ ] *Interactive Lab: Kafka Partition, Consumer Group & Backpressure Stream* (`interactive-simulations/04-kafka-stream-simulator/`)

### [Module 05: Reliability, Resiliency & Fault Tolerance](docs/05-resilience-fault-tolerance/)
- [ ] **05.1 Failure Modes in Distributed Systems** (Grey Failures, Cascading Failures, Retry Storms, Slow Dependencies)
- [ ] **05.2 Rate Limiting & Throttling Algorithms** (Token Bucket, Leaky Bucket, Fixed Window, Sliding Window Log & Counter, Distributed Redis Lua)
- [ ] **05.3 Circuit Breaker Pattern** (Closed → Open → Half-Open State Machine)
- [ ] **05.4 Timeouts, Retries, Exponential Backoff, Full Jitter & Hedged Requests**
- [ ] **05.5 Bulkheads, Load Shedding, Graceful Degradation & Chaos Engineering**
- [ ] **05.6 Multi-Region Architecture & Disaster Recovery** (Active-Active vs Active-Passive, Failover, RPO / RTO)
- [ ] *Interactive Lab: Rate Limiter Sandbox & Circuit Breaker State Machine* (`interactive-simulations/05-resilience-simulator/`)

### [Module 06: Distributed Consensus, Coordination & Time](docs/06-distributed-consensus-coordination/)
- [ ] **06.1 The Consensus Problem & Impossibility Results** (Two Generals' Problem, FLP Impossibility, Byzantine Faults)
- [ ] **06.2 Consensus Algorithms: Raft & Paxos Internals** (Leader Election, Terms, Log Replication, Split Votes, Safety Properties)
- [ ] **06.3 Distributed Locking, Leases & Fencing Tokens** (ZooKeeper / etcd vs Redlock, Split-Brain Prevention)
- [ ] **06.4 Gossip Protocols, Membership & Failure Detection** (SWIM, Phi Accrual Failure Detector, Anti-Entropy Merkle Trees)
- [ ] **06.5 Distributed Unique ID Generation** (Twitter Snowflake, UUIDv7, ULID, Flicker Ticket Servers)
- [ ] **06.6 Time & Event Ordering in Distributed Systems** (Clock Skew, NTP, Lamport Timestamps, Vector Clocks, Google TrueTime)
- [ ] *Interactive Lab: Raft Consensus & Leader Election Playground* (`interactive-simulations/06-raft-consensus-simulator/`)

### [Module 07: Search, Real-Time, Geospatial & Data Pipelines](docs/07-search-realtime-geospatial/)
- [ ] **07.1 Full-Text Search & Inverted Indexes** (Tokenization, BM25, Scatter-Gather in Elasticsearch, Prefix Tries)
- [ ] **07.2 Real-Time Connections at Scale** (1M+ Concurrent WebSockets, Fan-Out Gateways, Heartbeats & Presence Systems)
- [ ] **07.3 Geospatial Indexing & Proximity Search** (Geohash, Quadtree, R-Tree, Google S2 / Uber H3)
- [ ] **07.4 Batch vs Stream Processing & Windowing** (Lambda vs Kappa Architecture, Tumbling/Sliding/Session Windows, Watermarks & Late Data)
- [ ] *Interactive Lab: Geohash, Quadtree & Inverted Index Visualizer* (`interactive-simulations/07-geospatial-search-simulator/`)

### [Module 08: Security, Observability & Production Engineering](docs/08-security-observability-production/)
- [ ] **08.1 AuthN & AuthZ at Scale** (Stateful Sessions vs JWT, OAuth 2.0 / OIDC, RBAC/ABAC, API Keys, SSO)
- [ ] **08.2 Network & Data Security** (mTLS, Zero Trust, Envelope Encryption, KMS, WAF & L3/L4/L7 DDoS Mitigation)
- [ ] **08.3 The Three Pillars of Observability** (Structured Logging, Metrics/Histograms & Tail Latency p95/p99, Distributed Tracing & OpenTelemetry)
- [ ] **08.4 Reliability Targets: SLIs, SLOs, SLAs & Error Budgets**
- [ ] **08.5 Zero-Downtime Deployments & Migrations** (Blue-Green, Canary, Shadow Traffic, Feature Flags, Expand-Contract DB Migrations)
- [ ] *Interactive Lab: Distributed Trace Waterfall & p99 Tail-Latency Explorer* (`interactive-simulations/08-observability-trace-simulator/`)

### [Module 09: Modern AI & ML Infrastructure System Design](docs/09-ai-ml-systems/)
- [ ] **09.1 Vector Search & Hybrid Retrieval at Scale** (ANN Indexing: HNSW & IVF-PQ, Dense + BM25 Fusion, Reranking Pipelines)
- [ ] **09.2 LLM Serving & Inference Systems** (Prefill vs Decode, KV Cache, PagedAttention, Continuous Batching, Speculative Decoding)
- [ ] **09.3 AI Gateways, Routing & Guardrails** (Multi-Model Routing, Semantic Caching, Token Rate Limiting, Async Evals)
- [ ] **09.4 Recommendation & Ranking Pipelines** (Candidate Generation, Feature Stores, Two-Tower Models, Real-Time Re-Ranking)
- [ ] *Interactive Lab: Hybrid Retrieval & LLM Continuous Batching Visualizer* (`interactive-simulations/09-ai-inference-simulator/`)

### [Module 10: End-to-End System Design Case Studies](docs/10-case-studies/)
- [ ] **10.1 TinyURL / URL Shortener & Pastebin** (Base62, Hashing vs KGS, Read-Heavy Caching)
- [ ] **10.2 Distributed Rate Limiter Service** (Edge Enforcement, Redis Lua Atomicity, Fail-Open vs Fail-Closed)
- [ ] **10.3 Search Autocomplete (Typeahead) & Distributed Web Crawler** (Tries, Politeness, URL Frontier, Dedup)
- [ ] **10.4 Multi-Channel Notification & Alerting Engine** (Push/SMS/Email Fan-out, Priority Queues, Deduplication)
- [ ] **10.5 Real-Time Chat System** (WhatsApp / Slack / Discord — WebSocket Routing, Offline Sync, Group Fan-out)
- [ ] **10.6 Social Media Newsfeed** (X / Instagram — Hybrid Fan-out on Write vs Read, Celebrity Problem)
- [ ] **10.7 Cloud File Storage & Sync** (Dropbox / Google Drive — Block Chunking, Content-Addressed Dedup, Delta Sync)
- [ ] **10.8 Video Streaming Platform** (YouTube / Netflix — Transcoding DAG, Adaptive Bitrate HLS/DASH, ISP Open Connect CDN)
- [ ] **10.9 Flash Sale & Ticket Booking Engine** (Ticketmaster / BookMyShow — Seat Hold TTL, Optimistic/Distributed Locks, Virtual Waiting Room)
- [ ] **10.10 Ride-Sharing Dispatch System** (Uber / Ola — Geospatial Index, Driver Location Stream, Matching & ETA)
- [ ] **10.11 Payment Gateway, Wallet & Double-Entry Ledger** (Stripe / UPI — Strict Idempotency, Exactly-Once Ledger, Async Reconciliation)
- [ ] **10.12 Real-Time Collaborative Document Editor** (Google Docs — Operational Transformation vs CRDTs)
- [ ] **10.13 Distributed Metrics & Log Monitoring System** (Datadog / Prometheus — High-Write Time-Series Ingestion, Downsampling & Alerting)
- [ ] **10.14 Ad Click Aggregator & Real-Time Gaming Leaderboard** (Stream Windowing, Reconciliation, Redis Sorted Sets)
- [ ] **10.15 Production Enterprise RAG & AI Copilot Platform** (Hybrid Search, Multi-Tenant ACLs, Streaming Tokens & Observability)

---

## 📚 Internal Reference Library (`.references/` - Gitignored)

- `karanpratapsingh-system-design/`: Cloned from `https://github.com/karanpratapsingh/system-design` (architecture diagrams, module outlines, references).
- `bytebytego/explaining-9-types-of-api-testing.md`: Extracted guide on smoke, contract, stress, and security testing.
- Industry whitepapers (Dynamo, GFS, MapReduce, Bigtable, Raft, Kafka, Spanner, Gorilla, Borg, vLLM/PagedAttention).