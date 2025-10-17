> System consistently delivers correct results even when things go wrong, despite hardware failures, software bugs, or human errors.

Analogy: 
	Ideal Pizza Shop is **RELIABLE** because they deliver hot and fresh pizza on time despite being busy or having issues at the bakery.

#### Why **RELIABILITY** matters?
- User Trust -
	- If a pizza shop messes up orders regularly, customers stop ordering.
- Revenue Impact
	- One failed delivery loses that sale plus future orders
- Reputation
		- Unreliable systems reflect poorly on engineering teams
-  Business Survival
		- Consistent failures mean bankruptcy
 
#### **Real-World Example**
**Scenario**: Your pizza shop (microservice) processes 1000 orders/hour
**Without Reliability:**
	- Single database instance
	- No retry logic
	- One application server
	- **Result**: 2% orders fail = 20 unhappy customers/hour
**With Reliability:**
	- Primary + replica database with auto-failover
	- Circuit breaker with 3 retry attempts
	- 3 application instances behind load balancer
	- Dead letter queue for failed orders
	- **Result**: 0.01% failure rate = 1 failure per 10,000 orders
**The Cost:**
	- 3x compute resources
	- 2x database instances
	- Additional monitoring/queue infrastructure
	- **Business Decision**: Worth it? For pizza shop making ₹500/order, absolutely!

#### How **RELIABILITY** is achieved?
- Redundancy / Replication
	 **Multiple instances of Machine** across Availability Zones (Multiple Ovens (instances), backup ingredients, extra delivery drivers). 
- Quality / Health checks
	 **Implement liveness/readiness** probes using K8s (Verify orders before boxing, temperature checks).
- Fault Detection	
	 Use Prometheus + Grafana for **real-time alerts** (Manager monitors all stations, alerts when issues arise)
- Quick Recovery / Graceful Degradation 
	 **Serve cached data** when database is slow (Spare oven ready, backup suppliers on speed dial)
- Error Handling 
	 Correct the error and retry (Wrong order? Remake it immediately and deliver free)
- Transaction Management
	 Use Spring @Transactional with proper isolation levels. [Further Reading](https://docs.spring.io/spring-framework/reference/data-access/transaction.html)
-  Idempotency
	  Design APIs to handle duplicate requests safely (If the customer places similar order twice, consider it as one)

####  **RELIABILITY** Trade-offs?
-  Cost Vs Availability 
	1. Multi-region deployment doubles infrastructure costs. (Multiple ovens cost more upfront)
	2. Running 10 instances instead 2, increases server bill (Extra staff increases payroll)
	3. Additional monitoring tools require licenses (Premium ingredients are expensive)
	4. Backup systems sit idle most of the time
	
- Performance vs Consistency
	1. Strong consistency (waiting for all replicas) slows response time
	2. Eventual consistency is faster but might show stale data
	3. Example: Pizza shop confirms order immediately vs waiting for kitchen confirmation
	
-  Complexity vs Simplicity
	1. More redundancy means more components to manage
	2. Complex failover logic introduces new bugs
	3. Simple systems are easier to reason about but less resilient
### RELIABILITY Patterns
	-- TO Be hadled -- 
