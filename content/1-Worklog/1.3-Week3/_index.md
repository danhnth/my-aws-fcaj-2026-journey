---
title: "Week 3 Worklog"
date: 2026-07-04
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Get introduced to Infrastructure as Code (IaC) with Terraform — core concepts, HCL syntax, and state management.
* Plan the "Insecure-by-Design" project architecture and define the misconfiguration scenarios.
* Design and write Terraform modules for the vulnerable baseline infrastructure.
* Begin provisioning the initial set of intentionally misconfigured AWS resources.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (29/06) | - Introduction to Terraform <br>&emsp; + What is IaC? Why Terraform? <br>&emsp; + HCL syntax — resources, data sources, variables, outputs <br>&emsp; + Terraform workflow (init, plan, apply, destroy) <br> - Install Terraform and configure AWS provider | 29/06/2026 | 29/06/2026 | <https://developer.hashicorp.com/terraform/docs> |
| Tue (30/06) | - Learn Terraform state management <br>&emsp; + Local vs remote state <br>&emsp; + State locking with DynamoDB <br> - Set up an S3 backend for Terraform state <br> - Write a simple Terraform script to create an S3 bucket and EC2 instance | 30/06/2026 | 30/06/2026 | <https://developer.hashicorp.com/terraform/language/state> |
| Wed (01/07) | - Design the "Insecure-by-Design" architecture <br> - Identify misconfiguration scenarios to deploy: <br>&emsp; + Public S3 bucket with sensitive data <br>&emsp; + Over-privileged IAM role with wildcard (*) permissions <br>&emsp; + EC2 instance with public SSH access and no restrictions <br> - Define the project directory structure and module layout | 01/07/2026 | 01/07/2026 | |
| Thu (02/07) | - Write Terraform modules for the vulnerable baseline: <br>&emsp; + Module: `vpc` — basic VPC with public subnets <br>&emsp; + Module: `s3-vulnerable` — public S3 bucket with permissive bucket policy <br>&emsp; + Module: `iam-vulnerable` — IAM role with wildcard permissions | 02/07/2026 | 03/07/2026 | |
| Fri (03/07) | - Write the Terraform root module and wire dependencies <br> - Create `terraform.tfvars` with environment configuration <br> - Run `terraform init` and `terraform plan` to validate the configuration <br> - Review planned resources with the mentor | 03/07/2026 | 03/07/2026 | |
| Sat (04/07) | - **Practice:** <br>&emsp; + Run `terraform apply` to deploy the vulnerable baseline <br>&emsp; + Verify the deployed resources in the AWS Console <br>&emsp; + Test public S3 bucket accessibility from an external browser <br> - Document initial findings and plan Week 4 tasks | 04/07/2026 | 04/07/2026 | |

### Week 3 Achievements:

* Understood Terraform fundamentals — wrote HCL configuration files using resources, variables, outputs, and data sources. Successfully ran the full Terraform workflow (init, plan, apply, destroy) on test resources.

* Set up a remote backend for Terraform state using an S3 bucket with DynamoDB state locking, enabling safe team collaboration and state persistence.

* Designed the Insecure-by-Design project architecture covering three core misconfiguration scenarios: a public S3 bucket, an over-privileged IAM role, and a publicly accessible EC2 instance.

* Structured the Terraform project with reusable modules:
  * `modules/vpc/` — a basic VPC with a public subnet, Internet Gateway, and route table
  * `modules/s3-vulnerable/` — an S3 bucket configured with a bucket policy allowing public read access
  * `modules/iam-vulnerable/` — an IAM role with `Action: "*"` and `Resource: "*"` attached (simulating an over-privileged DevOps role)
  * `modules/ec2-vulnerable/` — an EC2 instance launched in a public subnet with SSH access from 0.0.0.0/0

* Successfully deployed the vulnerable baseline with `terraform apply` and verified:
  * S3 bucket is publicly listable and readable from a non-AWS browser session (simulated attacker view)
  * IAM role allows any action on any resource (verified via IAM Policy Simulator)
  * EC2 instance has unrestricted SSH inbound from all IPs

* Documented the current security posture and confirmed that AWS Trusted Advisor and Security Hub (once enabled) would flag these as critical findings.

* Prepared the groundwork for Week 4 — deploying additional vulnerable resources and expanding monitoring coverage.
