

✅ Interview Answer — SLI, SLO, SLA

👉 SLI (Service Level Indicator)
SLI is the actual metric used to measure service performance, such as availability, latency, or error rate.
Example: If 99 out of 100 requests succeed, the SLI is 99% availability.

👉 SLO (Service Level Objective)
SLO is the target or goal for the SLI that the team aims to achieve.
Example: The objective may be to maintain 99.9% availability.

👉 SLA (Service Level Agreement)
SLA is a formal agreement with customers that defines the promised service level and penalties if it is not met.
Example: If availability drops below 99.9%, the company may provide service credits.


---
👉 “Recently, we had a P2 incident where Spinnaker became unavailable, blocking deployment pipelines.”

👉 “I confirmed the outage, escalated to the Incident Manager, and began troubleshooting.”

👉 “Cluster and dependent services were healthy, but Orca pods showed timeout and high latency errors.”

👉 “Since Orca orchestrates pipeline execution, its degradation impacted the entire platform.”

👉 “I performed a controlled restart of the affected pods, which restored normal operation.”

👉 “After recovery, we reviewed logs and metrics to identify the underlying cause and prevent recurrence.”


After restarting Orca to restore service, we performed RCA and implemented preventive measures such as scaling the service, tuning resource limits, verifying health probes, reviewing timeout configurations, and enhancing monitoring. This ensured similar failures would be detected early or avoided entirely.”

---

👉 “We had a P2 incident where SonarQube scan jobs started failing, blocking CI/CD pipelines.”

👉 “I verified that the SonarQube application pods were healthy, so the issue appeared during the scanning phase.”

👉 “Error logs indicated that required dependency JAR files could not be downloaded from the artifact repository.”

👉 “Previously, these dependencies were fetched from Nexus, but the repository became unreachable or unavailable.”

👉 “To restore service quickly, we bundled the required JARs into the build image, rebuilt the Docker image, and redeployed it.”

👉 “After deployment, scans resumed successfully and pipelines were unblocked.”

----

✅ 1) Describe a Sev-1 production incident you handled

In a Sev-1 incident where the application became unavailable for all users, I first confirmed the outage through monitoring and alerts. I declared an incident, assembled the response team, and initiated mitigation by rolling back the recent deployment. After stabilizing the service, we analyzed logs and metrics to identify the root cause, documented the findings, and implemented preventive measures to avoid recurrence.

✅ 2) How do you reduce MTTR?

- improving monitoring and alerting for faster detection, 
- maintaining runbooks for common issues, 
- automating recovery actions where possible, and ensuring clear incident response processes. Effective communication 
- quick decision-making during incidents also significantly reduce resolution time.

✅ 3) How do you perform Root Cause Analysis (RCA)?

After restoring service,
 - I collect logs, metrics, and timelines to reconstruct what happened.
 - I identify the triggering event, contributing factors, and why safeguards failed. Then I document the root cause, impact, and corrective actions, focusing on systemic improvements rather than individual mistakes.

✅ 4) What is a blameless postmortem?

- A blameless postmortem is a review conducted after an incident that focuses on learning and prevention instead of blaming individuals.
- The goal is to identify process gaps, technical weaknesses, and improvement areas so the organization becomes more reliable.

✅ 5) How do you prioritize incidents during multiple failures?

- I prioritize based on business impact, number of affected users, severity of service degradation, and SLA risk. 
- Critical customer-facing outages take highest priority, followed by partial service disruptions, while non-critical issues are handled later or delegated.

✅ 6) How do you communicate outages to stakeholders?

- I provide clear, concise updates that include impact, affected services, current status, mitigation steps, and estimated recovery time.
-  Updates are shared at regular intervals through predefined communication channels to ensure transparency and avoid confusion.

✅ 7) What metrics define system reliability?

- Key reliability metrics include availability (uptime), latency (response time), error rate, throughput, and system saturation. 
- These metrics collectively indicate how well the system performs under normal and peak conditions.

✅ 8) Difference between availability and reliability

- Availability measures how often the system is accessible and operational, usually expressed as uptime percentage. 
- Reliability refers to the system’s ability to function correctly without failures over time, including consistency and error-free operation.

✅ 9) What is an error budget? How do you use it?

- An error budget is the acceptable amount of failure derived from the SLO. It represents how much downtime or errors are allowed within a period. If the error budget is being consumed too quickly, we slow or stop risky changes and focus on stability improvements.

✅ 10) When would you stop feature releases due to reliability risk?

I would pause releases when the error budget is exhausted, when system stability is degrading, during ongoing major incidents, or when monitoring shows increased failure rates. In such cases, the priority shifts to restoring reliability before introducing new changes.




## 1. What problem does SRE actually solve in an organization?

- SRE ensures systems are reliable, scalable, and efficient while still allowing teams to ship fast. It balances feature velocity and stability using engineering principles, not manual ops.

## 2. How is SRE different from traditional DevOps?

- DevOps focuses on culture and collaboration. SRE focuses on measurable reliability, SLIs/SLOs, and automation backed by data.

## 3. What is an SLI in real production terms?

- An SLI is a quantifiable metric that reflects user experience, such as request latency, error rate, or availability.

## 4. How do you choose the right SLI?

- Choose metrics that users actually feel, not internal metrics. For example, HTTP success rate is better than CPU usage.

## 5. What is an SLO and why is it critical?

- An SLO defines the acceptable reliability target (e.g., 99.9% availability). It sets a clear expectation between engineering and business.

## 6. What happens if an SLO is consistently violated?

- Feature releases should slow down or stop, and focus should shift to reliability improvements. This prevents burnout and outages.

## 7. What is an error budget in simple terms?

- Error budget is the allowed amount of failure within an SLO. It gives teams freedom to innovate while controlling risk.

## 8. How do error budgets influence release decisions?

- If the error budget is healthy, teams can release aggressively. If exhausted, releases are frozen until stability improves.

## 9. Why is monitoring not enough without alerting?

- Monitoring shows what happened. Alerting ensures someone acts immediately when user impact occurs.

## 10. What makes a good alert in production?

- A good alert is actionable, urgent, and user-impacting. Alerts on symptoms, not causes.

## 11. Why is alert fatigue dangerous?

- Too many alerts cause engineers to ignore real incidents, increasing MTTR and outage impact.

## 12. How do you reduce alert noise in real systems?

- Use SLO-based alerts, remove low-value alerts, and rely on aggregation and deduplication.

## 13. What is MTTR and why do leaders care about it?

- MTTR (Mean Time To Recover) measures how fast systems recover, not just how often they fail.

## 14. How do you practically reduce MTTR?

- Improve observability, create runbooks, automate remediation, and ensure clear ownership during incidents.

## 15. What is a production incident from an SRE view?

- Any event that impacts users or violates SLOs, not just system crashes.

## 16. How do you run an effective incident response?

- Use a clear incident commander, reduce communication chaos, focus on mitigation first, root cause later.

## 17. What is a blameless postmortem and why does it matter?

- It focuses on system failures, not people, enabling learning and preventing repeat incidents.

## 18. What should a good postmortem always include?

- Timeline, impact, root cause, contributing factors, and clear action items with owners.

## 19. How do you prevent the same incident from happening again?

- Fix systemic issues, add safeguards, improve alerts, and automate where possible.

## 20. Why is automation a core SRE principle?

- Manual work does not scale. Automation reduces human error and improves consistency.

## 21. What kind of tasks should never be manual in SRE?

- Deployments, rollbacks, scaling, certificate renewals, and routine recovery actions.

## 22. How do you decide what to automate first?

- Automate frequent, error-prone, and high-impact tasks first.

## 23. What is toil in SRE language?

- Toil is manual, repetitive work that produces no long-term value.

## 24. How much toil is acceptable in an SRE team?

- Google recommends less than 50% toil. More than that blocks innovation and reliability improvements.

## 25. How do you measure toil practically?

- Track time spent on manual ops, tickets, and repetitive tasks during sprints.

## 26. Why is capacity planning important for SRE?

- It prevents outages caused by resource exhaustion and avoids over-spending.

## 27. How do you plan capacity in cloud environments?

- Use historical trends, growth projections, and load testing—not guesswork.

# 28. What role does chaos engineering play in SRE?

- It validates system resilience by intentionally injecting failures in a controlled way.

## 29. When should chaos testing be avoided?

- During incidents, peak business hours, or when systems lack proper monitoring.

## 30. What is the difference between availability and reliability?

- Availability is uptime. Reliability includes correctness, latency, and consistency.

## 31. Why is 100% availability a bad goal?

- It is unrealistic and expensive. It prevents innovation and leads to burnout.

## 32. How do you balance reliability vs feature velocity?

- Use error budgets to make data-driven decisions, not emotional ones.

## 33. What metrics matter most to SRE leadership?

- SLO compliance, MTTR, incident frequency, and customer impact.

## 34. Why is logging critical during incidents?

- Logs provide context and root cause clues that metrics alone cannot.

## 35. How do you design logs for production systems?

- Use structured logs, include request IDs, and log meaningful events—not noise.

## 36. What is observability beyond monitoring?

- Observability explains why something happened, not just that it happened.

## 37. How do metrics, logs, and traces work together?

- Metrics show trends, logs show details, traces show request flow.

## 38. Why do SREs prefer pull-based monitoring like Prometheus?

- It is more reliable, easier to scale, and safer than push models.

## 39. How do you handle deployments safely in SRE?

- Use canary releases, blue-green deployments, and automated rollbacks.

## 40. Why are runbooks important during incidents?

- They reduce decision-making time and help any engineer act quickly.

## 41. What makes a runbook effective?

- Clear steps, validation commands, rollback actions, and ownership details.

## 42. How do you prevent configuration drift?

- Use Infrastructure as Code and enforce version control.

## 43. Why do SREs care about immutability?

- Immutable systems reduce drift, simplify debugging, and improve reliability.

## 44. How do you handle third-party dependency failures?

Use timeouts, retries with backoff, circuit breakers, and fallbacks.

## 45. What is graceful degradation?

- The system continues to work with reduced functionality instead of failing completely.

## 46. Why are load tests important before production?

- They expose bottlenecks early and prevent surprise outages.

## 47. What is a single point of failure (SPOF)?

- Any component whose failure brings down the entire system.

## 48. How do you eliminate SPOFs?

- Add redundancy, health checks, and automated failover.

## 49. What mindset separates strong SREs from average ones?

- Strong SREs think in systems and failure modes, not tools.

## 50. What is the ultimate goal of an SRE team?

- Keep users happy by delivering reliable systems at sustainable speed.


## What is Recovery Time Objective (RTO), and how is it used to design disaster recovery solutions?
- RTO defines the target time to restore service after a disruption.
- It helps organizations design disaster recovery strategies, backups, failover, and incident response to minimize downtime.
- For example, critical systems like payment platforms may have an RTO of a few minutes, while internal tools may tolerate several hour


## What is Recovery Point Objective (RPO), and how is it used in disaster recovery planning?”
or
## What is Recovery Point Objective (RPO), and how does it influence backup and disaster recovery strategies?”

- Recovery Point Objective (RPO) defines how much data loss a system can tolerate during a disaster. It determines backup frequency and replication strategy. For example, an RPO of 1 hour means the system should not lose more than one hour of data.”













