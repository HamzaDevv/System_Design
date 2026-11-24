# 🎯 45-Minute System Design Interview Rubric & Strategy

A standard 45-minute System Design Interview is **not** a quiz with one right answer. It is an evaluation of how you communicate, decompose ambiguity, make rational trade-offs, and navigate engineering compromises.

---

## ⏱️ The 45-Minute Time Allocation Matrix

```
[00:00 - 05:00] Step 1: Scope & Clarification (Functional & Non-Functional)
[05:00 - 10:00] Step 2: Back-of-the-Envelope Calculations & Capacity Planning
[10:00 - 25:00] Step 3: High-Level Architecture & API / Data Models
[25:00 - 40:00] Step 4: Deep Dive Bottlenecks, Edge Cases, & Failure Modes
[40:00 - 45:00] Wrap-up: Summary, Monitoring, Metrics, & Candidate Q&A
```

---

## 🧭 Step-by-Step Execution Playbook

### Step 1: Scoping & Requirements (5 mins)
Never jump straight into drawing boxes.
- **Clarify Core Functional Requirements**:
  - *"What are the top 2-3 essential features the user must be able to do?"* (e.g., Shorten URL, redirect URL, view click analytics).
  - Explicitly declare out-of-scope features: *"For now, custom expiration rules or user billing are out of scope unless needed."*
- **Clarify Non-Functional Requirements**:
  - High Availability vs. Strong Consistency (CAP Theorem).
  - Target Latency (e.g., `< 20ms` for redirects).
  - Throughput scale (e.g., Read-heavy with 100:1 read-to-write ratio).

### Step 2: Back-of-the-Envelope Calculations (5 mins)
- Daily Active Users (DAU) $\rightarrow$ QPS (Average & Peak).
- Daily Writes $\rightarrow$ Storage over 5 years.
- Ingress/Egress Bandwidth.
- Cache memory estimation (20% Pareto rule).

### Step 3: High-Level Architecture (15 mins)
- Define clean APIs (`POST /v1/urls`, `GET /{short_url}`).
- Select database type (SQL vs NoSQL: justify why based on query patterns, ACID requirements, and schema flexibility).
- Draw the end-to-end component flow:
  1. Client $\rightarrow$ DNS $\rightarrow$ CDN (static assets).
  2. Load Balancer $\rightarrow$ API Gateway / Auth.
  3. Stateless Application Servers.
  4. Cache Layer (Redis / Memcached).
  5. Persistent Storage & Replicas.
  6. Message Queue / Event Bus for asynchronous tasks.

### Step 4: Deep Dive & Edge Cases (15 mins)
Proactively lead the conversation into the hard engineering trade-offs:
- **Single Points of Failure (SPOF)**: What if the primary database dies? How does failover happen?
- **Data Partitioning / Sharding**: How do we split data across multiple shards? What is the partition key? What about hot partitions (celebrity problem)?
- **Concurrency & Race Conditions**: How do we handle double-booking, duplicate clicks, or distributed state mutations? (Optimistic locking, distributed locks, idempotent keys).
- **Failure Recovery**: How do we handle cascading service degradation? (Circuit breakers, exponential backoff, rate limiters, fallback responses).

---

## 🚦 Interviewer Evaluation Signals

| Signal | Positive Indicator (Strong Hire) | Negative Red Flag (No Hire) |
|---|---|---|
| **Ambiguity Handling** | Asks clarifying questions, drives scope definition | Starts designing before knowing scale or features |
| **System Breadth** | Explains entire flow from Client to DB & Async workers | Stays trapped in one small component |
| **System Depth** | Knows database index internals, network overhead, cache caveats | Uses buzzwords (e.g. "Just put Kafka here") without knowing why |
| **Trade-offs** | Clearly articulates pros and cons of two approaches | Declares one technology as "always the best" |
| **Collaboration** | Treats interviewer as fellow team lead, checks in often | Monologues defensively, ignores interviewer prompts |
