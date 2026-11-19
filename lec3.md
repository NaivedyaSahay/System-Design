# Lecture Notes: Load Balancing & System Scaling

**Source:** *"What is LOAD BALANCING? ⚖️"* by Gaurav Sen (`http://www.youtube.com/watch?v=K0Ta65OqQkY`)

---

## 1. Client, Server, and Scaling Basics

* **Server vs. Client:** A **server** is a machine or program that listens for incoming **requests** from a **client** (such as a mobile app), runs backend logic/algorithms (for example, a facial recognition filter), and sends back a **response** `[00:01:29]`.
* **Scalability:** When traffic spikes and a single machine can no longer process all incoming requests, you add more servers ($n$ servers) to share the workload `[00:02:12]`.
* **Load Balancing:** The process of evenly distributing incoming requests across $n$ servers so no single node gets overwhelmed `[00:03:23]`.

---

## 2. Naive Modulo Hashing ($\text{hash}(\text{request}) \bmod n$)

### Mechanism
1. Each incoming request has a unique identifier or key `[00:03:58]`.
2. A **hash function** converts that ID into an integer `[00:04:34]`.
3. Taking $\text{hash\_value} \bmod n$ (the remainder after dividing by $n$ servers) yields a target server index in the range $[0, n-1]$ `[00:04:46]`.

### Concrete Example ($n = 4$ servers: $s_0, s_1, s_2, s_3$)
* For request hash values such as $3, 15, 12$:
  * $3 \bmod 4 = 3 \implies s_3$ `[00:05:05]`
  * $15 \bmod 4 = 3 \implies s_3$
  * $12 \bmod 4 = 0 \implies s_0$

### Ideal Case
With uniform request IDs and a well-behaved hash function, load spreads roughly equally ($1/n$ share per server) as long as the server count $n$ remains constant `[00:06:19]`.

---

## 3. The Scaling Problem ("Splitting the Pie")

### Adding a Server ($n: 4 \to 5$)
Changing $n$ from $4$ to $5$ alters the divisor in the modulo operation, causing almost every request mapping to change `[00:06:39]`.

### The 100-Bucket Pie Analogy
* **With 4 servers ($n = 4$):** Each server controls $25\%$ of the key space ($25$ buckets each) `[00:08:00]`.
* **Adding a 5th server ($n = 5$):** Each server should ideally control $20\%$ of the key space ($20$ buckets each).
* **The Problem:** Modulo hashing does not simply transfer $5$ buckets from each existing server to $s_4$. Instead, shifting the divisor recalculates virtually every single bucket mapping across the entire key space `[00:08:25], [00:10:06]`.

---

## 4. Request Stickiness & Local Cache Invalidation

* **Request Stickiness:** In production systems, request IDs often map to user identities. Consistent routing ensures that requests from the same user repeatedly reach the same server `[00:10:35], [00:11:06]`.
* **Local Caching:** If a user repeatedly routes to the same server, that server can store user-specific data (such as profile details or session state) in its **local cache**, avoiding expensive database calls `[00:11:17]`.
* **Failure Mode (Cache Dump):** When $n$ changes under naive modulo hashing, users get remapped to different servers `[00:11:54]`. As a result:
  * Local caches become ineffective (cache misses skyrocket).
  * Backend databases experience sudden traffic spikes as servers re-fetch user data.

---

## 5. Summary & Key Takeaways

| Concept | Description |
| :--- | :--- |
| **Load Balancing** | Distributing incoming requests evenly across multiple servers. |
| **Sticky Routing** | Directing the same user to the same server to utilize local caching. |
| **Modulo Hashing Limit** | Changing $n$ in $\text{hash}(r) \bmod n$ scrambles almost all key assignments. |
| **Consistent Hashing Goal** | Ensure that adding or removing a server reassigns only a small fraction ($\approx 1/n$) of keys, preserving existing caches `[00:12:19]`. |