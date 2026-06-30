---
title: "Week 1 Worklog"
date: 2026-06-25
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* Get acquainted with FCAJ members, mentors, and the program structure.
* Understand the internship rules, regulations, and reporting expectations.
* Learn the fundamentals of AWS Cloud — global infrastructure, core service categories, and the shared responsibility model.
* Set up an AWS Free Tier account, the AWS Management Console, and AWS CLI.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (15/06) | - Orientation & introduction to FCAJ program <br> - Meet mentor and team members <br> - Read internship unit rules and regulations | 15/06/2026 | 15/06/2026 | |
| Tue (16/06) | - Learn AWS Cloud fundamentals <br>&emsp; + Global infrastructure (Regions, AZs, Edge locations) <br>&emsp; + Shared Responsibility Model <br>&emsp; + Core service categories <br> - Review the FCAJ Cloud Journey learning path | 16/06/2026 | 16/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed (17/06) | - Create AWS Free Tier account <br> - Explore AWS Management Console <br> - Set up billing alerts and MFA on root account | 17/06/2026 | 17/06/2026 | <https://aws.amazon.com/free/> |
| Thu (18/06) | - Install & configure AWS CLI <br>&emsp; + IAM user & Access Key creation <br>&emsp; + Configure default region and output format <br> - Practice basic AWS CLI commands | 18/06/2026 | 18/06/2026 | <https://docs.aws.amazon.com/cli/> |
| Fri (19/06) | - Learn about EC2 fundamentals <br>&emsp; + Instance types, AMI, EBS <br>&emsp; + Security Groups, Key Pairs <br>&emsp; + SSH connection methods <br> - Launch a t2.micro EC2 instance and connect via SSH | 19/06/2026 | 20/06/2026 | <https://docs.aws.amazon.com/ec2/> |
| Sat (20/06) | - **Practice:** <br>&emsp; + Launch and terminate EC2 instances <br>&emsp; + Attach/detach EBS volumes <br>&emsp; + Configure Security Group rules <br> - Review and document Week 1 learnings | 20/06/2026 | 20/06/2026 | |

### Week 1 Achievements:

* Gained a solid understanding of AWS global infrastructure and the Shared Responsibility Model.

* Successfully created and secured an AWS Free Tier account with MFA and billing alerts.

* Became proficient with the AWS Management Console — navigating services, finding resources, and understanding the dashboard.

* Installed and configured AWS CLI with proper IAM credentials, including:
  * Access Key & Secret Key setup
  * Default region and output format (JSON)
  * Named profiles for multiple environments

* Used AWS CLI to perform basic operations:
  * Check caller identity (`aws sts get-caller-identity`)
  * List available regions (`aws ec2 describe-regions`)
  * Describe EC2 instances and key pairs
  * Create and manage S3 buckets via CLI

* Launched an EC2 instance (t2.micro, Amazon Linux 2), connected via SSH, and attached an additional EBS volume.

* Understood the difference between ephemeral and persistent storage, and how Security Groups act as a virtual firewall.

* Set up the foundation for the coming weeks — AWS account ready, CLI configured, and core compute/storage/networking concepts in place.
