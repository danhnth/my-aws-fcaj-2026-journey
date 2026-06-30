---
title: "Week 2 Worklog"
date: 2026-06-27
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Understand AWS Identity and Access Management (IAM) in depth — users, groups, roles, policies, and the principle of least privilege.
* Learn about S3 security — bucket policies, ACLs, public access settings, and encryption.
* Explore VPC fundamentals — subnets, route tables, Internet Gateway, NAT Gateway, and security best practices.
* Get introduced to CloudTrail for API activity logging and monitoring.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (22/06) | - Deep-dive into IAM <br>&emsp; + Users, Groups, Roles, Policies <br>&emsp; + Managed vs Inline policies <br>&emsp; + IAM Policy Simulator <br> - Create IAM users with different permission levels | 22/06/2026 | 22/06/2026 | <https://docs.aws.amazon.com/IAM/> |
| Tue (23/06) | - Learn about IAM Roles and trust policies <br> - Practice: cross-account access with IAM Roles <br> - Understand IAM best practices (least privilege, password policies, access keys rotation) | 23/06/2026 | 23/06/2026 | <https://docs.aws.amazon.com/IAM/> |
| Wed (24/06) | - Learn Amazon S3 in depth <br>&emsp; + Bucket policies vs ACLs <br>&emsp; + Block Public Access settings <br>&emsp; + Server-side encryption (SSE-S3, SSE-KMS, SSE-C) <br> - Practice: create public vs private S3 buckets | 24/06/2026 | 24/06/2026 | <https://docs.aws.amazon.com/s3/> |
| Thu (25/06) | - Learn VPC fundamentals <br>&emsp; + VPC, Subnets (public/private) <br>&emsp; + Route Tables, Internet Gateway <br>&emsp; + NAT Gateway, Security Groups, NACLs <br> - Launch EC2 instances in public and private subnets | 25/06/2026 | 26/06/2026 | <https://docs.aws.amazon.com/vpc/> |
| Fri (26/06) | - Introduction to AWS CloudTrail <br>&emsp; + What is CloudTrail? (management vs data events) <br>&emsp; + Create a trail and log to S3 <br>&emsp; + CloudTrail Insights <br> - Review CloudTrail logs in the Console | 26/06/2026 | 26/06/2026 | <https://docs.aws.amazon.com/cloudtrail/> |
| Sat (27/06) | - **Practice:** <br>&emsp; + Combine IAM + S3 + VPC in a mini-lab <br>&emsp; + Configure VPC Flow Logs for network monitoring <br> - Review and document Week 2 learnings | 27/06/2026 | 27/06/2026 | |

### Week 2 Achievements:

* Gained a thorough understanding of IAM — created users with granular permissions, set up groups with managed policies, and tested access boundaries with the IAM Policy Simulator.

* Understood the difference between IAM Roles and Users, and practiced cross-account role assumption.

* Applied IAM best practices: enforced a strong password policy, rotated access keys, and removed unused credentials.

* Mastered S3 security controls:
  * Blocked public access at the account level and bucket level
  * Configured bucket policies for specific IP-based and role-based access
  * Enabled SSE-S3 encryption on all buckets
  * Tested public access attempts to verify Block Public Access settings

* Built a custom VPC from scratch with:
  * Public and private subnets across two Availability Zones
  * Internet Gateway for public subnet access
  * NAT Gateway for private subnet outbound connectivity
  * Security Groups with least-privilege rules and Network ACLs for subnet-level filtering

* Launched EC2 instances in both public and private subnets to verify connectivity patterns (SSH to public instance, private instance outbound through NAT).

* Set up AWS CloudTrail with a management-event-only trail logging to an S3 bucket, and explored CloudTrail event history to understand API activity recording.

* Configured VPC Flow Logs and analyzed sample log entries to understand allowed/denied traffic patterns.
