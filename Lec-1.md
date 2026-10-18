# Core Principles of System Design

This video explains the core principles of **system design** using the analogy of managing a growing pizza restaurant. It introduces 10 fundamental concepts engineers use to build systems that are scalable, reliable, and maintainable.

## 10 Fundamental Concepts

### 1. Vertical Scaling
Increasing the capacity of a single resource to handle more load.

**Pizza restaurant analogy:** Asking one chef to work faster or equipping the same chef with better tools.

### 2. Preprocessing
Performing tasks ahead of time—often during non-peak hours—to improve efficiency when demand is high.

**Example:** Using scheduled tasks such as **cron jobs** to process data in advance.

### 3. Backup Servers
Maintaining redundant resources to reduce the risk of a single point of failure.

**Pizza restaurant analogy:** Having a backup chef available if the main chef cannot work.

### 4. Horizontal Scaling
Adding more machines or instances of the same type to distribute work across multiple resources.

**Pizza restaurant analogy:** Hiring more chefs so several orders can be prepared simultaneously.

### 5. Microservices
Dividing an application into smaller, specialized services, each with a distinct responsibility.

**Pizza restaurant analogy:** Assigning separate teams to order management, cooking, payments, and delivery coordination.

### 6. Distributed Systems
Running components across multiple machines or locations to improve fault tolerance, availability, and potentially response times.

**Example:** Deploying services across different servers or regions.

### 7. Load Balancing
Distributing incoming requests among available resources to avoid overloading a single server and improve utilization.

**Pizza restaurant analogy:** A coordinator directing each new order to an available chef.

### 8. Decoupling
Separating components so they can evolve, operate, or change independently with fewer unintended effects on other components.

**Pizza restaurant analogy:** Keeping the restaurant's kitchen operations separate from the delivery service.

### 9. Logging and Metrics
Recording events and measuring system behavior to understand health, performance, errors, and resource usage.

- **Logging:** Records events and details about what happened.
- **Metrics:** Measures values such as request latency, error rate, and CPU usage.

### 10. Extensibility
Designing a system so new features and requirements can be added with minimal disruption to existing functionality.

**Pizza restaurant analogy:** Making it easy to add new menu items or introduce online ordering.

## High-Level Design vs. Low-Level Design

| Aspect | High-Level Design (HLD) | Low-Level Design (LLD) |
|---|---|---|
| Focus | Overall architecture | Internal implementation details |
| Main concerns | Components, services, databases, communication, and scalability | Classes, methods, interfaces, data structures, and design patterns |
| Perspective | How the major parts fit together | How individual components are built |
| Typical outputs | Architecture diagrams and component interactions | Class diagrams, sequence diagrams, and detailed design specifications |

## Key Takeaway

Good system design balances **scalability, reliability, maintainability, performance, and flexibility**. High-level design defines the overall structure and interactions of a system, while low-level design describes the implementation details within its components.
