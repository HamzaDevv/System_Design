# ⏱️ Latency Numbers Every System Designer Must Know

In system design, **order-of-magnitude intuition** separates junior engineers from senior distributed systems architects. You don't need to memorize exact nanoseconds, but you **must** understand the relative scale difference between CPU registers, RAM, SSDs, spinning disks, and network roundtrips.

---

## 📊 The Canonical Latency Table (Jeff Dean & Peter Norvig)

| Operation | Real Time | Scaled (If 1 CPU Cycle = 1 Second) | Intuitive Analogy |
|---|---|---|---|
| **L1 cache reference** | `0.5 ns` | 0.5 sec | A single human heartbeat |
| **Branch mispredict** | `5 ns` | 5 sec | Yawning |
| **L2 cache reference** | `7 ns` | 7 sec | Taking a sip of water |
| **Mutex lock / unlock** | `25 ns` | 25 sec | Washing your hands |
| **Main memory (RAM) reference** | `100 ns` | 100 sec (~1.6 min) | Brewing a cup of coffee |
| **Compress 1KB with Zippy / Snappy** | `10 µs` | 2.8 hours | Watching a movie |
| **Send 1KB over 1 Gbps network** | `10 µs` | 2.8 hours | Taking a long hike |
| **Read 1 MB sequentially from RAM** | `250 µs` | 2.9 days | A weekend holiday |
| **SSD random read** | `150 µs` | 1.7 days | A mini-vacation |
| **Roundtrip within same datacenter** | `500 µs` | 5.8 days | A full work week |
| **Read 1 MB sequentially from SSD** | `1 ms` | 11.6 days | Two weeks off |
| **HDD (Mechanical Disk) seek** | `10 ms` | 3.8 months | An entire academic semester |
| **Read 1 MB sequentially from HDD** | `20 ms` | 7.7 months | Growing an agricultural crop |
| **Send packet CA -> Netherlands -> CA** | `150 ms` | **4.75 years!** | Completing an entire undergraduate degree! |

---

## 🧠 The 5 Big Takeaways for System Design

### 1. Memory is Fast, Disk is Slow, Network is Ancient
- Accessing RAM is roughly **100,000x faster** than a mechanical disk seek and **1,000x faster** than an SSD random read.
- This is why caching tiers (Redis / Memcached) are non-negotiable for high-read applications.

### 2. Sequential vs. Random I/O is Night and Day
- Sequential reads from modern NVMe SSDs can exceed **3,000 MB/s**, while random disk seeks are orders of magnitude slower.
- Database engines like LSM-Trees (used in Cassandra, RocksDB, Bigtable) deliberately convert random writes into sequential append-only writes to leverage this physical property.

### 3. Compression is Almost "Free" Compared to Network Transmission
- Compressing 1KB takes ~10 microseconds. Sending uncompressed data across the internet can take 50–150 milliseconds.
- Always compress payloads over WAN (gzip, zstd, Brotli, Snappy).

### 4. Cross-Datacenter Roundtrips Dominate Response Latency
- Light travels in fiber optic cable at ~200 km/ms (~2/3 speed of light in vacuum).
- No amount of software optimization can beat physics: a packet between US East and Europe takes at least 70–100ms roundtrip.
- **System Design Rule**: Keep user data close to the edge using CDNs and multi-region deployments with read-local architectures.

### 5. Datacenter Roundtrips are Not Zero
- A simple internal RPC between two microservices within the same datacenter costs ~0.5ms.
- If a single user request cascades through 20 synchronous microservice calls in series, you just added 10ms of pure wire latency, excluding any actual work!
- **System Design Rule**: Favor parallel fan-outs (`Promise.all` / async fan-out) or batching over serial microservice ping-pong.
