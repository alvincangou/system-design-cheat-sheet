# System Design Engineering Cheat Sheet & Playbook

An interactive, first-principles cheat sheet covering distributed systems mechanics, database internals, resiliency patterns, and production case studies.

## 🚀 Hosted Live on GitHub Pages
This repository contains a standalone, zero-dependency `index.html` file pre-configured for instant free hosting on GitHub Pages.


cheat sheet is live at [https://alvincangou.github.io/system-design-cheat-sheet/](https://alvincangou.github.io/system-design-cheat-sheet/) !

## 📌 What's Included inside the Playbook

### 1. ☁️ Multi-Cloud Equivalence Matrix (AWS vs GCP vs Azure vs Open Source)
Direct component mapping across **Amazon Web Services**, **Google Cloud Platform**, **Microsoft Azure**, and **Open Source** primitives:
* Relational DBs (Aurora / Cloud SQL / Azure SQL / Postgres)
* Distributed SQL (Spanner / Aurora Global / Cosmos DB / CockroachDB)
* NoSQL Key-Value (DynamoDB / Bigtable / Cosmos DB / ScyllaDB)
* In-Memory Caches (ElastiCache / Memorystore / Azure Cache / Redis)
* Event Streams (MSK / PubSub / Event Hubs / Kafka)
* Task Queues (SQS / Cloud Tasks / Service Bus / RabbitMQ)

### 2. 7 ByteByteGo-Grade Case Studies
* **Discord:** Moving from Cassandra to ScyllaDB + Rust Request Coalescing (177 -> 72 nodes, P99 down to 15ms).
* **Slack:** Scaling MySQL horizontal sharding via Vitess gRPC multiplexing.
* **Netflix:** Global video CDN pre-positioning (Open Connect) & AWS control plane.
* **Uber:** Real-time geospatial dispatch via Uber H3 Hexagons + Ringpop.
* **Google Cloud Spanner:** TrueTime Atomic Clock hardware ($\epsilon \le 1	ext{ms}$) & Multi-Paxos consensus.
* **WhatsApp / Meta:** Handling 2 billion active users on Erlang OTP BEAM processes.
* **Stripe:** Idempotent payment processing engine via distributed Redis locks & headers.

### 3. Deep Architectural Primitives
* **Storage Engines:** B-Trees vs. LSM Trees, Bloom Filters, $WAF/RAF/SAF$ Amplification metrics.
* **Distributed Consistency:** PACELC Theorem, Quorum Mathematics ($W + R > N$).
* **Resiliency & Thundering Herd Defenses:** Single-Flight Request Coalescing, XFetch Probabilistic Early Expiration.
* **Relational Scaling:** OS thread starvation vs. Vitess gRPC multiplexing.
* **Geospatial Infrastructure:** Uber H3 Hexagonal Grid vs. Geohash boundary distortion.
* **Incident Failure Matrix:** Symptom -> Root Cause -> Immediate Mitigation -> Strategic Fix.
