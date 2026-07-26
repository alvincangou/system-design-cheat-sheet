# System Design Engineering Cheat Sheet & Playbook

An interactive, first-principles cheat sheet covering distributed systems mechanics, database internals, resiliency patterns, production case studies, and architecture anti-patterns — now expanded with **DDIA-grade deep-dives** and interactive tooling.

## 🚀 Hosted Live on GitHub Pages
This repository contains a standalone, zero-dependency `index.html` file pre-configured for instant free hosting on GitHub Pages.

The playbook is live at [https://alvincangou.github.io/system-design-cheat-sheet/](https://alvincangou.github.io/system-design-cheat-sheet/)!

## 📌 What's Included (16 Modules)

### 1. ☁️ Multi-Cloud Equivalence Matrix (AWS vs GCP vs Azure vs Open Source)
Direct component mapping across **Amazon Web Services**, **Google Cloud Platform**, **Microsoft Azure**, and **Open Source** primitives:
* Relational DBs (Aurora / Cloud SQL / Azure SQL / Postgres)
* Distributed SQL (Spanner / Aurora Global / Cosmos DB / CockroachDB)
* NoSQL Key-Value (DynamoDB / Bigtable / Cosmos DB / ScyllaDB)
* In-Memory Caches (ElastiCache / Memorystore / Azure Cache / Redis)
* Event Streams (MSK / PubSub / Event Hubs / Kafka)
* Task Queues (SQS / Cloud Tasks / Service Bus / RabbitMQ)

### 2. 🗄️ Storage Engine Internals
* **B-Trees vs. LSM Trees:** Page updates in-place vs. append-only MemTable & SSTable flush cycles
* **Bloom Filter False Positive Rate Formula:** `p ≈ (1 - e^(-kn/m))^k`
* **Amplification Metrics:** WAF (Write), RAF (Read), SAF (Space)

### 3. 🔤 Data Encoding & Schema Evolution (DDIA Deep-Dive)
* **Avro vs. Protobuf vs. Thrift:** Wire format comparison with field tags vs. schema embedding
* **Schema Registry Pattern:** Zero-downtime rolling deployments with compatibility checks (BACKWARD, FORWARD, FULL)
* **JSON/XML vs. Binary:** 3–10x bandwidth and parsing cost analysis

### 4. 🔄 Advanced Replication & Consensus Edge Cases
* **Multi-Leader Replication:** LWW hazards, Operational Transformation (Google Docs), CRDTs
* **Leaderless Quorums:** Sloppy quorums, hinted handoff, read-repair
* **Anti-Entropy:** Merkle tree-based partition sync
* **CRDT Deep-Dive:** PN-Counter and OR-Set merge semantics

### 5. 🛡️ Transactions, Concurrency Control & Isolation Levels
* **Isolation Matrix:** Dirty Read → Non-Repeatable Read → Phantom Read → Write Skew → Lost Update
* **MVCC & Serializable Snapshot Isolation (SSI):** Write-skew anomaly detection
* **Distributed Transactions:** 2PC blocking nature vs. Saga Pattern (Choreography vs. Orchestration)

### 6. ⚖️ Distributed Consistency & Consensus
* **PACELC Theorem:** Partition tradeoffs (CAP) and normal operating latencies
* **Quorum Math:** `W + R > N` for strong linearizable consistency

### 7. ⚡ Resiliency & Thundering Herd Defenses
* **Single-Flight Request Coalescing:** Go `singleflight` / Rust proxy pattern
* **XFetch Probabilistic Early Expiration:** `-β · δ · ln(random()) > TTL - now`

### 8. 🖥️ Relational Scaling & Connection Multiplexing
* **OS Thread Starvation:** 10,000 connections × thread stack = RAM exhaustion
* **Vitess Architecture:** VTGate gRPC multiplexing to VTTablet

### 9. 🌐 Event Streams & Geospatial Partitioning
* **Task Queues (RabbitMQ, SQS):** Destructive consumption, non-replayable
* **Commit Logs (Kafka, Pub/Sub):** Immutable append-only, replayable history
* **Uber H3 Hexagonal Grid:** 16 resolution levels, equal-distance neighbors

### 10. 📊 Batch & Stream Processing (DDIA Deep-Dive)
* **Change Data Capture (CDC):** Debezium + WAL-based streaming
* **Dual-Write Problem & Outbox Pattern:** Atomic DB + message writes
* **Event Sourcing:** Append-only event log, state derivation by replay
* **Lambda vs. Kappa Architecture:** Two-pipeline vs. single-stream tradeoffs

### 11. 🧮 Interactive Back-of-the-Envelope Estimator
Live calculator with inputs for:
* Daily Active Users (DAU), Actions/User/Day, Avg Payload Size
* Read/Write Ratio, Peak Multiplier
* **Outputs:** Average QPS, Peak QPS, Bandwidth (MB/sec), 1-Year Storage, Read/Write QPS split

### 12. 🚦 Rate Limiting & Load Balancing Algorithms
* **Rate Limiters:** Token Bucket, Leaky Bucket, Fixed Window Counter, Sliding Window Log, Sliding Window Counter (Redis Sorted Set)
* **Load Balancers:** L4 (Transport) vs. L7 (Application), Consistent Hashing with Virtual Nodes

### 13. ⚠️ Architecture Anti-Patterns & Common Traps
* **Resume-Driven Development (RDD):** Adopting FAANG tools for low-traffic apps
* **Premature Distributed Monoliths:** 20 microservices before domain boundaries are understood
* **Cloud Bill Shock & Over-Provisioning:** Hidden egress, IOPS, and provisioned concurrency costs
* **The "NoSQL is Web Scale" Fallacy:** Forcing relational workloads into document stores

### 14. 🏛️ 7 ByteByteGo-Grade Case Studies (with Interactive Drawers)
Click any case study to open a **deep-dive drawer** with Mermaid architecture diagrams, problem/solution breakdowns, key metrics, and configuration tuning tips:
* **Discord:** Moving from Cassandra to ScyllaDB + Rust Request Coalescing (177 → 72 nodes, P99 down to 15ms)
* **Slack:** Scaling MySQL horizontal sharding via Vitess gRPC multiplexing
* **Netflix:** Global video CDN pre-positioning (Open Connect) & AWS control plane
* **Uber:** Real-time geospatial dispatch via Uber H3 Hexagons + Ringpop
* **Google Cloud Spanner:** TrueTime Atomic Clock hardware & Multi-Paxos consensus
* **WhatsApp / Meta:** 2 billion active users on Erlang OTP BEAM processes (~2KB RAM per connection)
* **Stripe:** Idempotent payment processing via Redis distributed locks & Idempotency-Key headers

### 15. 🚨 Incident & Failure Mitigation Matrix
Quick-reference table: Symptom → Root Cause → Immediate Mitigation → Strategic Long-Term Fix
* Cache Stampede, JVM GC Pauses, Thread Starvation, Hot Partitions, Schema Evolution Failures, Data Loss

### 16. 🛤️ On-Premise to Cloud Migration Paradigms
Comprehensive coverage of enterprise migration patterns and cloud-native transformations:
* **Architectural Shifts:** Batch-Scheduled → Event-Driven (EDA), Monolithic/VMs → Serverless & Microservices
* **Security & Identity:** Perimeter Security → Zero Trust, Hardcoded Secrets → Dynamic Key Management (Secrets Manager, KMS, Key Vault)
* **State Management:** Local Config → Externalized Configuration (Parameter Store, AppConfig), Stateful Disks → Ephemeral Compute + Object Storage
* **Deployment & Observability:** Manual Deployments → Immutable Infrastructure (IaC) with Blue/Green & Canary, Siloed Logs → Distributed Tracing (X-Ray, Cloud Trace, App Insights)
* **Migration Execution:** Big Bang Cutover → Strangler Fig Pattern, Manual SQL Dumps → Zero-Downtime CDC (Debezium, AWS DMS)
* **Enterprise Realities:** The "6 Rs" Framework (Rehost, Replatform, Refactor, Repurchase, Retire, Retain), Data Gravity & Petabyte Transfer (Snowball, Transfer Appliance, Data Box), Dedicated Network Interconnects (Direct Connect, Cloud Interconnect, ExpressRoute), Governance & Landing Zones (Control Tower, Resource Folders, Management Groups)
* **Comprehensive Translation Matrix:** 11-row mapping of on-premise concepts to AWS/GCP/Azure cloud-native equivalents

## ✨ Interactive Features
* **🔍 Search & Filter:** Real-time text search across all modules with category filtering
* **📐 Mermaid.js Diagrams:** Interactive SVG architecture diagrams in deep-dive drawers
* **📖 Study Progress Tracker:** localStorage-persistent checkboxes per module with progress bar
* **🧮 Live Calculator:** Back-of-the-envelope scale metric estimation
* **📂 Expandable Drawers:** Click case studies for architecture diagrams, failure trees, and config tuning tips
* **🔄 Toggle Cards:** Expandable Avro vs. Protobuf comparison

## 🛠️ Tech Stack
* **Single-file HTML** — Zero dependencies, no build step, instant GitHub Pages deployment
* **Tailwind CSS** (CDN) — Utility-first responsive design
* **Font Awesome 6** (CDN) — Icon library
* **Mermaid.js 10** (CDN) — Interactive SVG architecture diagrams
* **localStorage** — Study progress persistence across sessions

## 📄 License
MIT — Free to use, modify, and share.