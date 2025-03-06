**Postmortem: Web Stack Outage Due to Database Connection Exhaustion**

**Issue Summary:**  
- **Duration:** March 5, 2025, 14:30 - 16:15 UTC (1 hour 45 minutes)  
- **Impact:** Our primary web application was significantly degraded. 70% of users experienced timeouts or slow responses while attempting to log in or access key features. API clients also experienced intermittent failures.  
- **Root Cause:** A sudden surge in traffic led to the exhaustion of available database connections due to an improperly configured connection pool.

---

**Timeline:**  
- **14:30 GMT:** Monitoring alerts triggered due to increased response times and 5xx errors.  
- **14:35 GMT:** On-call engineer noticed high database CPU usage and connection saturation.  
- **14:40 GMT:** Initial assumption: database instance overload. Read replica scaling was attempted.  
- **14:50 GMT:** Engineers began investigating recent deployments for regressions but found no direct correlation.  
- **15:10 GMT:** Escalated to the database team; further debugging revealed an excessive number of open connections.  
- **15:25 GMT:** Identified that connection pooling settings had a hard cap, preventing proper reuse of connections under high load.  
- **15:45 GMT:** Connection pooling limits were adjusted, and idle connections were aggressively closed.  
- **16:00 GMT:** Application performance returned to normal.  
- **16:15 GMT:** Incident closed after verification and monitoring stabilization.  

---

**Root Cause and Resolution:**  
- The database connection pool was configured with a low maximum limit of active connections (100), while the application scaled up beyond this threshold, leading to connection starvation.  
- The application continued creating new connections, but since the pool limit was reached, queries were queuing and timing out.  
- To resolve the issue:
  - The connection pool limit was increased dynamically to accommodate peak traffic.
  - Idle connections were closed more aggressively to free up resources.
  - Database-level monitoring was improved to track connection pool saturation in real-time.  

---

**Corrective and Preventative Measures:**  
- **Improvements:**
  - Enhance monitoring to track connection pool utilization and alert earlier on saturation.
  - Establish an auto-scaling policy for the connection pool based on load.
  - Review database connection handling to ensure proper reuse and cleanup of connections.  

- **Action Items:**
  - [ ] Implement database connection pool auto-scaling.
  - [ ] Add real-time alerts for connection pool exhaustion.
  - [ ] Conduct a post-incident review with engineering teams to improve response time.
  - [ ] Update documentation on proper database connection management best practices.
  
This postmortem ensures that we learn from this incident and prevent similar outages in the future.

