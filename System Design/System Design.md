---
mindmap-plugin: basic
---

# System Design Pillars

## [[RELIABILITY]] (Correctness under stated conditions)
1. Fault Tolerance (Zero-downtime during failures)
2. Fault Prevention (Avoid failures)
3. Fault Detection (Identify failures)
4. Fault Recovery (Restore operations)
5. Redundancy (Eliminate single points of failure)
6. Data Integrity (Accurate, consistent data)

## [[AVAILABILITY]] (System uptime and accessibility)
1. High Availability (99.9%, 99.99%, 99.999%)
2. Load Balancing (Distribute traffic)
3. Clustering (Multiple servers as one)
4. Disaster Recovery (Catastrophic failure planning)
5. Maintenance Windows (Planned downtime)
6. Geographic Distribution (Multi-region)

## [[SCALABILITY]] (Handle growth)
1. Horizontal Scaling (Add machines)
2. Vertical Scaling (Bigger machines)
3. Database Scalability (Sharding, replicas)
4. Caching Strategies (Reduce load)
5. Asynchronous Processing (Decouple operations)
6. Microservices Architecture (Independent scaling)

## [[PERFORMANCE]] (Speed and efficiency)
1. Response Time (Latency optimization)
2. Throughput (Volume per time)
3. Resource Utilization (CPU, memory, I/O)
4. Concurrency (Parallel processing)
5. Query Optimization (Database efficiency)
6. Frontend Performance (Client-side optimization)

## MAINTAINABILITY (Easy to modify and operate
 1. Modularity (Independent components)
 2. Observability (Logs, metrics, traces)
 3. Testing (Quality assurance)
 4. Documentation (Knowledge sharing)
 5. Code Quality (Clean, readable code)
 6. Deployment Automation (CI/CD)

## SECURITY (Protection from threats)
1. Authentication (Verify identity)
2. Authorization (Control access)
3. Data Protection (Encryption, masking)
4. Network Security (Firewalls, VPN)
5. Application Security (Prevent vulnerabilities)
6. Monitoring & Incident Response (Detect threats)

## CONSISTENCY (Data agreement)
1. Strong Consistency (Immediate agreement)
2. Eventual Consistency (Converge over time)
3. Causal Consistency (Causally ordered)
4. Transactional Consistency (ACID)
5. Distributed Consensus (Agreement protocols)

## PARTITION TOLERANCE (Handle network splits)
1. Network Partition Handling (Split-brain)
2. CAP Theorem Trade-offs (CP vs AP vs CA)
3. Data Replication Strategies (Master-slave, multi-master)

## Relationships Between Pillars
- 1. Complementary Relationships
	- **Reliability + Availability** = Highly reliable systems are usually highly available
	- **Scalability + Performance** = Scaling improves capacity, optimization improves speed
	- **Security + Maintainability** = Secure code is often well-documented and tested
- 2. Trade-off Relationships
	- **Consistency ↔ Availability** (CAP theorem)
	- **Performance ↔ Security** (Encryption adds overhead)
	- **Scalability ↔ Consistency** (Distributed systems harder to keep consistent)