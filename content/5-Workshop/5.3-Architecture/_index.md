---
title : "Architecture"
date : 2026-06-26 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Architecture Diagram

The data flow and security detection pipeline for this workshop is as follows:

```text
[User/Attacker] ──(Misconfigurations)──> [ EC2 / S3 Bucket / IAM Role ]
                                                  │
                                            (Log Capture)
                                                  ▼
                                           [ AWS CloudTrail ]
                                                  │
                                          (Behavior Analysis)
                                                  ▼
                                          [ Amazon GuardDuty ]
                                                  │
                                        (Aggregation & Scoring)
                                                  ▼
                                          [ AWS Security Hub ]
```

#### Architecture Flow Explanation

1. **Vulnerability Entry** — An attacker or user exploits misconfigurations on EC2, S3, or IAM (e.g., public S3 bucket, global SSH access, `*/*` IAM policy).
2. **Log Capture** — AWS CloudTrail records all API calls, including malicious or unauthorized actions.
3. **Threat Detection** — Amazon GuardDuty analyzes behavior and logs to detect threats and anomalies.
4. **Aggregation & Assessment** — AWS Security Hub aggregates findings from GuardDuty and automatically scores compliance against the CIS AWS Foundations Benchmark.

#### AWS Services Used

| Service | Role |
|---------|------|
| **AWS CloudTrail** | Centralized API logging and audit trail |
| **Amazon GuardDuty** | ML-powered threat detection |
| **AWS Security Hub** | Centralized security findings and compliance assessment |
| **Amazon S3** | Storage for CloudTrail logs and potentially vulnerable data |
| **Amazon EC2** | Compute instances (with intentional misconfigurations initially) |
| **AWS IAM** | Identity and access management (including over-privileged roles) |
