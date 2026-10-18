# System Design Notes

> 🍕 **System design, through a growing pizza restaurant:** The video uses a familiar business to explain how engineers build systems that scale, stay reliable, and adapt over time.

## 1. Scale & Performance
* **Vertical scaling:** Increase the capacity of one resource—like asking a chef to work faster—to handle more demand.
* **Horizontal scaling:** Add more machines of the same type so the work can be shared.
* **Preprocessing:** Schedule work, such as cron jobs, during quieter hours to improve efficiency during peak times.

## 2. Reliability & Traffic
* **Backup servers:** Keep redundant resources available to avoid a single point of failure—like having a backup chef.
* **Distributed systems:** Spread components across locations to improve fault tolerance and response times.
* **Load balancing:** Route incoming requests to the most available resource.

## 3. Architecture & Boundaries
* **Microservices:** Split a system into specialized, manageable units, each with a distinct responsibility.
* **Decoupling:** Separate independent components—like the pizza shop and delivery agents—so they can change without disrupting one another.

## 4. Observe & Evolve
* **Logging & metrics:** Track events and analyze data to monitor system health and performance.
* **Extensibility:** Design the system so it can accommodate new requirements and features more easily.

---

> 🧭 **Two levels of design**
> * **High-level design:** Architecture and how systems interact.
> * **Low-level design:** Code, classes, and object-oriented patterns.
