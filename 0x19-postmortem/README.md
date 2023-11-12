Postmortem: Web Stack Debugging Outage



Issue Summary:

- Duration: 
  - Start Time: [05/10/23 at 07:00 PM] [GMT+1]
  - End Time:  [07/10/23 at 12:00 AM] [GMT+1]

- Impact:
  - The outage affected the core authentication service, rendering users unable to log in.
  - Approximately 30% of users experienced login failures, leading to a degradation in service availability.

- Root Cause:
  - The outage was caused by a misconfiguration in the load balancer settings, leading to a disproportionate distribution of authentication requests to one of the backend servers.

Timeline:

- Detection:
  - Detected at [05/10/23 at 07:00 PM] through an automated monitoring alert indicating a spike in failed authentication attempts.

- Actions Taken:
  - Investigated server logs to identify any anomalies in authentication patterns.
  - Initially assumed a database issue and checked database connections and performance.
  - Engaged the network team to analyse load balancer configurations.
  
- Misleading Paths:
  - Initially focused on database-related issues due to a recent schema update, leading to a delay in identifying the root cause.
  - Investigated potential DDoS attacks, which proved to be a false trail.

- Escalation:
  - Escalated the incident to the network and infrastructure team as load balancer misconfiguration became evident.

- Resolution:
  - Temporarily disabled the problematic server in the load balancer rotation, redistributing traffic evenly.
  - Implemented a quick fix to adjust load balancer settings to prevent recurrence.
  - Monitored the system to ensure stability.

Root Cause and Resolution:

- Root Cause:
  - The misconfiguration in the load balancer resulted from an incomplete update during routine maintenance, causing uneven distribution of authentication requests.

- Resolution:
  - Adjusted load balancer settings to evenly distribute traffic among backend servers.
  - Conducted a comprehensive audit of load balancer configurations to identify and rectify any potential issues.
  - Implemented a more robust deployment process to prevent similar misconfigurations in the future.

Corrective and Preventative Measures:

- Improvements/Fixes:
  - Enhance monitoring for load balancer configurations to detect anomalies promptly.
  - Implement automated testing for load balancer updates to ensure completeness and accuracy.
  - Conduct regular training sessions for the operations team to stay updated on best practices for system maintenance.

- Tasks:
  - Conduct a thorough review of the entire web stack for potential misconfigurations.
  - Document and share the incident's learnings with the team to foster awareness and prevent recurrence.
  - Implement redundancy measures for critical services to mitigate the impact of similar issues.

In conclusion, the outage highlighted the critical importance of meticulous configuration management and the need for proactive monitoring to ensure the seamless operation of our web stack. By implementing the outlined corrective and preventative measures, we aim to fortify our system against such incidents and further enhance the reliability of our services.
