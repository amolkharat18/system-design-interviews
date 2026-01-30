Meta system design interview: Design Instagram (with ex-Meta data engineer)

Link: https://www.youtube.com/watch?v=DXpJCh5_KT4

**The video is a mock Meta system design interview where an ex-Meta data engineer walks through how to design Instagram, focusing on scalability, reliability, and feature prioritization. The key takeaway is that system design interviews test structured thinking, trade-off analysis, and clarity in communication rather than just technical depth.**

---

## 📌 Key Takeaways from the Video

### 1. **Interview Context**
- The video simulates a **Meta system design interview**.
- The candidate is asked to **design Instagram** from scratch.
- Goal: Demonstrate **structured problem-solving** and **clear communication**.

### 2. **Breaking Down the Problem**
- Start with **requirements gathering**:
  - Core features: user profiles, photo sharing, feed, likes/comments.
  - Non-functional requirements: scalability, availability, latency.
- Clarify scope: focus on **MVP features first**, then expand.

### 3. **System Architecture**
- **High-level design**:
  - Client → API Gateway → Backend services.
  - Services: user service, photo service, feed service, notification service.
- **Data storage**:
  - Relational DB for user data.
  - Object storage (e.g., S3) for photos.
  - Caching (Redis/Memcached) for fast feed delivery.

### 4. **Scalability Considerations**
- **Sharding & replication** for databases to handle millions of users.
- **CDNs** for photo delivery to reduce latency worldwide.
- **Queue systems** (Kafka) for asynchronous tasks like notifications.

### 5. **Feed Generation**
- Two approaches:
  - **Pull model**: user requests feed, system aggregates posts.
  - **Push model**: pre-compute feeds and store them for quick retrieval.
- Trade-offs: push is faster but more storage-heavy; pull is flexible but slower.

### 6. **Reliability & Fault Tolerance**
- Use **load balancers** to distribute traffic.
- **Redundancy** in services to avoid single points of failure.
- Monitoring and alerting for system health.

### 7. **Interview Strategy Tips**
- Always **clarify requirements** before diving into design.
- **Communicate trade-offs** (e.g., latency vs. storage).
- Show **structured thinking**: start broad, then drill down.
- Keep solutions **practical and incremental**.

---

## 🎯 Why This Matters
- Meta and other big tech companies expect candidates to **think like system architects**, not just coders.
- The ability to **simplify complex systems** and explain design choices clearly is often more important than deep technical details.
- Practicing with real-world systems like Instagram helps candidates prepare for **open-ended design challenges**.

---
