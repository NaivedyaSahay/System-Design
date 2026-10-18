# Scaling & Cloud Infrastructure

> 💡 **The big idea:** Expose useful code through APIs, host it in the cloud, and scale infrastructure as demand grows.

### 1. APIs & the Cloud

* **API (Application Programming Interface):** Lets people use code over the internet instead of sharing the physical computer it runs on.
* **Request $\rightarrow$ Response:** A user sends input in a request; the server processes it and returns a response.
* **Why use the cloud?** A personal computer can go offline or need manual maintenance. Cloud providers supply remote computers and handle much of the underlying infrastructure, so teams can focus on their application.

### 2. Two Ways to Scale

**Scalability** is a system’s ability to handle a growing workload by adding hardware resources.

| Feature | Vertical Scaling · Up | Horizontal Scaling · Out |
| :--- | :--- | :--- |
| **What changes?** | Upgrade one machine | Add more machines and distribute requests |
| **Load balancing** | Not needed for a single machine | Needed to spread traffic across machines |
| **Resilience** | One machine is a single point of failure | Traffic can be redirected if a machine fails |
| **Communication** | Fast internal communication (IPC) | Network communication (RPC), which adds overhead |
| **Data consistency** | Simpler: data is on one system, making atomic transactions easier | More complex: data may need to be synchronized across machines |
| **Limits** | Constrained by the maximum size of one machine | Can grow by adding machines as demand increases |

### 3. The Practical Approach: Combine Both

Real systems often use horizontal scaling with reasonably powerful individual machines. This balances internal speed and simpler data handling with the resilience and growth potential of multiple machines.

> **Typical path:** Start by scaling vertically for simplicity. As usage grows, scale horizontally—while keeping each server powerful enough for its workload.