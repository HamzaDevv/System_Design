# 🌐 Module 00: Foundations, Network Protocols & Mental Models

> **The physical reality of distributed computing: Packets, Sockets, Latencies, and Estimations.**

---

## 🎯 Learning Objectives

Before architecting distributed databases, message brokers, or caching layers, you must master the physics and protocols of the internet:

1. **The Request-Response Lifecycle**: What happens when a user types `https://api.example.com/checkout` and presses Enter?
   - DNS Resolution (Recursive vs Authoritative DNS, Caching at OS/Browser/Router levels)
   - TCP 3-Way Handshake (`SYN` -> `SYN-ACK` -> `ACK`)
   - TLS 1.2 vs TLS 1.3 Cryptographic Handshake (Diffie-Hellman Key Exchange, Forward Secrecy)
   - HTTP Request processing, headers, keep-alive connections.
2. **Protocol Evolution**:
   - **HTTP/1.1**: Head-of-line (HOL) blocking at application level, connection pooling.
   - **HTTP/2**: Binary framing, stream multiplexing over a single TCP connection, HPACK header compression.
   - **HTTP/3 (QUIC over UDP)**: Eliminates TCP head-of-line blocking, 0-RTT connection resumption, connection migration across networks.
3. **Communication Paradigms**:
   - **REST**: Stateless, resource-oriented, standard HTTP verbs.
   - **gRPC & Protocol Buffers**: High-performance binary serialization, bi-directional streaming, strict schema contracts.
   - **Real-Time Duplex**: WebSockets vs Server-Sent Events (SSE) vs Long-Polling.
4. **Physical Latency Bounds**:
   - Memory vs Disk vs Network round-trips.
5. **Back-of-the-Envelope Estimation Framework**:
   - QPS, storage, bandwidth, and cache sizing calculations.

---

## 📂 Deep Dive Notes (Read in Sequence)

1. `01-request-lifecycle-dns-tcp-tls.md`
2. `02-http1-vs-http2-vs-http3-quic.md`
3. `03-rest-vs-grpc-vs-graphql.md`
4. `04-websockets-vs-sse-vs-polling.md`
5. `05-back-of-the-envelope-calculations.md`

---

## 🧪 Associated Visual Lab

- **Interactive Simulator**: Network Protocol Packet Flow & Handshake Visualizer.
