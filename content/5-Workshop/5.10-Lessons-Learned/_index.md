---
title : "Lessons Learned"
date : 2024-01-01 
weight : 10
chapter : false
pre : " <b> 5.10. </b> "
---

#### Lessons Learned & Future Development

**Challenges Encountered**

AWS security services do not update results in real-time. There is a latency of approximately **15 to 30 minutes** between making configuration changes and seeing updated findings in Security Hub and GuardDuty. This delay made rapid testing and validation cycles challenging.

**Key Takeaways**

- The importance of applying the **Principle of Least Privilege** from the very beginning of resource creation, rather than waiting for security alerts.
- AWS native security services (CloudTrail, GuardDuty, Security Hub) integrate seamlessly and provide comprehensive visibility when configured together.
- A substantial portion of cloud vulnerabilities stem from **configuration errors** rather than sophisticated attacks, making proper baseline configuration critical.

**Future Development Direction**

Instead of manually fixing vulnerabilities through the AWS Console (Manual Remediation), future work should explore automated remediation using **AWS Lambda** combined with **Amazon EventBridge** to automatically patch vulnerabilities as soon as Security Hub detects them (Auto-Remediation). This approach would:

1. Reduce the mean time to remediation (MTTR)
2. Minimize human error in the remediation process
3. Enable consistent enforcement of security policies at scale
