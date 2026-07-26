# System Design Engineering Cheat Sheet & Playbook

An interactive, first-principles cheat sheet covering distributed systems mechanics, database internals, resiliency patterns, and production case studies.

## 🚀 Hosted Live on GitHub Pages
This repository contains a standalone, zero-dependency `index.html` file pre-configured for instant free hosting on GitHub Pages.

### How to Deploy Your Own Copy in 2 Minutes:
1. Create a new repository on GitHub named `system-design-cheat-sheet`.
2. Upload the `index.html` and `README.md` files from this repository.
3. Go to **Settings** -> **Pages** in your GitHub repository.
4. Under **Source**, select `main` (or `master`) branch and `/ (root)`, then click **Save**.
5. Your cheat sheet will be live at `https://<your-username>.github.io/system-design-cheat-sheet/`!

## 📌 Features Included
* **Real-time Search & Filter:** Instant keyboard search across all algorithms and patterns.
* **Storage Engines:** B-Trees vs. LSM Trees, Bloom Filters, WAF/RAF trade-offs.
* **Distributed Consistency:** PACELC Theorem, Quorum math ($W + R > N$), Google Spanner TrueTime.
* **Resiliency Patterns:** Single-Flight Request Coalescing, XFetch Probabilistic Early Expiration.
* **Database Scaling:** Vitess connection multiplexing, thread starvation fixes.
* **Case Studies:** Discord (177 -> 72 ScyllaDB nodes), Slack (Vitess), Google Spanner.
* **Production Failure Matrix:** Immediate mitigations for high-scale incidents.
