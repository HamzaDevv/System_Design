# 📐 System Design Formulas, Sizing & Capacity Estimation Cheatsheet

Capacity estimation (Back-of-the-envelope calculation) proves to interviewers and architects that your design is physically grounded in reality rather than wishful thinking.

---

## ⚡ The "Rule of Thumb" Constants

### Time Constants
- **1 Day** = `24 × 3,600` = `86,400 seconds` $\approx \mathbf{10^5\text{ seconds}}$ *(Mental shortcut: $10^5$ or $86,400$)*
- **1 Month** $\approx 2.5 \times 10^6\text{ seconds}$
- **1 Year** $\approx 3.15 \times 10^7\text{ seconds} \approx \mathbf{3 \times 10^7\text{ seconds}}$

### Scale Constants (Powers of 10 vs Powers of 2)
| Prefix | Decimal (Storage/Network) | Binary |
|---|---|---|
| **Kilo (KB)** | $10^3 = 1,000$ | $2^{10} = 1,024$ |
| **Mega (MB)** | $10^6 = 1,000,000$ (Million) | $2^{20} \approx 1.05 \text{ Million}$ |
| **Giga (GB)** | $10^9 = 1,000,000,000$ (Billion) | $2^{30} \approx 1.07 \text{ Billion}$ |
| **Tera (TB)** | $10^{12} = 1\text{ Trillion}$ | $2^{40}$ |
| **Peta (PB)** | $10^{15} = 1\text{ Quadrillion}$ | $2^{50}$ |
| **Exa (EB)** | $10^{18}$ | $2^{60}$ |

---

## 🧮 Core Estimation Formulas

### 1. Throughput (QPS - Queries Per Second)
$$\text{Average QPS} = \frac{\text{Total Requests per Day}}{86,400} \approx \frac{\text{Total Requests per Day}}{100,000}$$

$$\text{Peak QPS} = \text{Average QPS} \times \text{Peak Multiplier (usually } 2\times \text{ to } 5\times\text{)}$$

#### Example:
- $100\text{ Million DAU}$, each user performs $10$ actions/day:
  - Total requests/day = $10^8 \times 10 = 10^9$ requests.
  - $\text{Average QPS} = \frac{10^9}{86,400} \approx 11,574\text{ requests/sec} \approx \mathbf{12,000\text{ QPS}}$.
  - $\text{Peak QPS} (2\times) \approx \mathbf{24,000\text{ QPS}}$.

---

### 2. Storage Estimation
$$\text{Daily Storage} = \text{Daily Writes} \times \text{Average Payload Size}$$
$$\text{Storage (5 Years)} = \text{Daily Storage} \times 365 \times 5 \times \text{Replication Factor (typically } 3\times\text{)}$$

#### Example:
- $100\text{M}$ posts created per day. Average metadata + text = $500\text{ Bytes}$.
- Daily storage = $10^8 \times 500\text{ B} = 50\text{ GB/day}$.
- 5-year storage = $50\text{ GB} \times 365 \times 5 \approx 91.25\text{ TB}$.
- With $3\times$ replication: $91.25 \times 3 \approx \mathbf{274\text{ TB}}$.

---

### 3. Network Bandwidth (Ingress / Egress)
$$\text{Ingress Bandwidth} = \text{Write QPS} \times \text{Average Request Size}$$
$$\text{Egress Bandwidth} = \text{Read QPS} \times \text{Average Response Size}$$

*(Remember: Bandwidth is traditionally reported in bits per second ($b/s$ or $bps$), where $1\text{ Byte} = 8\text{ bits}$)*

#### Example:
- Read QPS = $50,000\text{ req/sec}$. Average response = $10\text{ KB}$.
- Egress = $50,000 \times 10\text{ KB} = 500\text{ MB/sec}$.
- In bits: $500\text{ MB/s} \times 8 = 4\text{ Gbps}$ (Gigabits per second).

---

### 4. Memory & Cache Sizing (The 80/20 Pareto Rule)
Most online platforms follow the **Pareto Principle**: **20% of keys generate 80% of read traffic.**
To guarantee high cache hit ratios ($>90\%$), you want to hold that active $20\%$ of daily read volume in memory (Redis/Memcached).

$$\text{Cache Size} = 20\% \times (\text{Daily Read Requests} \times \text{Payload Size})$$

---

## 🛡️ Availability & SLAs: The "Nines" Table

High Availability (HA) guarantees are expressed in "nines".

| Availability Level | Downtime per Year | Downtime per Month | Downtime per Day | Feasible Architecture |
|---|---|---|---|---|
| **99% (Two 9s)** | 3.65 days | 7.31 hours | 14.4 minutes | Single instance with manual failover |
| **99.9% (Three 9s)** | 8.77 hours | 43.8 minutes | 1.44 minutes | Redundant instances, auto-restart |
| **99.99% (Four 9s)** | 52.6 minutes | 4.38 minutes | 8.64 seconds | Multi-AZ, automated health check failover |
| **99.999% (Five 9s)** | 5.26 minutes | 26.3 seconds | 0.86 seconds | Multi-Region active-active, zero single point of failure |
| **99.9999% (Six 9s)** | 31.5 seconds | 2.63 seconds | 0.086 seconds | Telco / Core Banking level engineering |

### Series vs. Parallel Availability Math
- **Components in Series** (all must succeed — e.g., API Gateway $\rightarrow$ App $\rightarrow$ Primary DB):
  $$A_{\text{total}} = A_1 \times A_2 \times \dots \times A_n$$
  *(Example: Two $99.9\%$ services in series drop total availability to $0.999 \times 0.999 \approx \mathbf{99.8\%}$!)*
- **Components in Parallel** (failover redundancy — succeeds if *at least one* survives):
  $$A_{\text{total}} = 1 - (1 - A_1)(1 - A_2)\dots(1 - A_n)$$
  *(Example: Two $99.9\%$ active-active instances yield $1 - (0.001)^2 = \mathbf{99.9999\%}$!)*
- **Availability vs. Reliability vs. Durability**:
  - **Availability**: Is the system responding to requests *right now*? (Measured in Nines of uptime).
  - **Reliability**: Is it returning *correct* results without silent corruption over time?
  - **Durability**: Are committed bytes preserved without permanent loss? (e.g., S3 promises `99.999999999%` — **11 nines** of durability via multi-AZ erasure coding, even when availability is `99.99%`).

---

## ⚙️ Concurrency, Tail Latency & Cloud FinOps Rules

### 5. Little's Law (Concurrency & Queue Sizing)
$$L = \lambda \times W$$
Where $L$ = average concurrent in-flight requests, $\lambda$ = arrival rate (QPS), $W$ = average latency per request (seconds).
*(Example: $10{,}000\text{ QPS}$ with $50\text{ ms}$ ($0.05\text{ s}$) latency requires **$500$ concurrent open connections/threads**! If downstream DB stalls to $2\text{ s}$, concurrency jumps $40\times$ to $20{,}000$ and exhausts connection pools.)*

### 6. Tail-Latency Amplification (Fan-Out)
If a single user request fans out to $N$ parallel leaf microservices and each has a $1\%$ slow tail ($p_{99}$):
$$P(\text{user experiences slow response}) = 1 - (0.99)^N$$
*(At $N = 100$ leaf calls, **$63.4\%$ of all user requests hit a tail spike!** That is why Google recommends **hedged requests**.)*

### 7. Cloud Economics & Transfer Costs (Back-of-the-Envelope FinOps)
- **Storage Tier Hierarchy** (relative monthly cost per GB): **RAM** ($\sim\$5\text{–}\$10$) $\gg$ **NVMe Block / EBS** ($\sim\$0.08\text{–}\$0.12$) $\gg$ **Object Storage / S3 Standard** ($\sim\$0.023$) $\gg$ **Cold Archive / Glacier** ($\sim\$0.001$).
- **Network Transfer Trap**: Cross-AZ traffic inside a cloud region typically costs $\sim\$0.01\text{–}\$0.02/\text{GB}$ *both ways*, and internet egress costs $\sim\$0.05\text{–}\$0.09/\text{GB}$. Topology-aware routing (AZ-local reads) and CDN offload save massive infrastructure spend at scale.
