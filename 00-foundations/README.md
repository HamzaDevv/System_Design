# 🌐 Module 00: Foundations, Networking & Mental Models

> [← Master Roadmap](../README.md) • [🏠 Simulation Hub](../index.html) • **Status: 🟢 Active (`2/6` Completed)**

Before architecting distributed databases, message brokers, or caching layers, you must master the physical constraints of the wire: DNS hierarchies, socket handshakes, protocol multiplexing, serialization overhead, and order-of-magnitude latency math.

---

## 📂 Topic Index

| # | Topic | Core Focus | Notes | Interactive Lab | Status |
|---|---|---|---|---|:---:|
| **00.1** | **The Request-Response Lifecycle** | DNS tree, BGP transit, TCP 3-way handshake, TLS 1.3 & HTTP | [Read Guide](./01-request-response-lifecycle/README.md) | [Launch Lab](./01-request-response-lifecycle/simulation.html) | ✅ Done |
| **00.2** | **Protocol Evolution** | HTTP/1.1 App HOL, HTTP/2 Multiplexing & TCP HOL, HTTP/3 QUIC | [Read Guide](./02-protocol-evolution/README.md) | [Launch Lab](./02-protocol-evolution/simulation.html) | ✅ Done |
| **00.3** | **Communication Paradigms** | REST vs gRPC & Protobuf vs GraphQL, Pagination & API Versioning | *Upcoming* | — | ⚪ Planned |
| **00.4** | **Duplex & Real-Time Transport** | WebSockets vs Server-Sent Events vs Long Polling vs WebRTC | *Upcoming* | — | ⚪ Planned |
| **00.5** | **Physical Latency, Throughput & Capacity Estimation** | Latency numbers, Little's Law, QPS / Storage / Bandwidth math | [Cheatsheet](../cheatsheets/system-design-formulas-and-estimations.md) | — | ⚪ Planned |
| **00.6** | **Serialization, Compression & Checksums** | JSON, Protobuf, Avro, Thrift, gzip/zstd, Schema Evolution | *Upcoming* | — | ⚪ Planned |
