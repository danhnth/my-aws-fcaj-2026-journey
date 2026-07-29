---
title: "Proposal"
date: 2026-06-30
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

In this section, you need to summarize the contents of the workshop that you **plan** to conduct.

# AWS Security Operations & Hardening Lab
## Insecure-by-Design to Managed Remediation

### 1. Executive Summary
The AWS Security Operations & Hardening lab approaches AWS Cloud through the lens of a **Cloud Security Engineer**, rather than simply deploying functioning resources. The core objective is to deploy a controlled, intentionally vulnerable cloud environment ("Insecure-by-Design"), monitor it using AWS native security services, and systematically harden it to meet enterprise security benchmarks such as the **CIS AWS Foundations Benchmark**. This hands-on workshop demonstrates the complete security lifecycle: from identifying misconfigurations, detecting threats in real-time, executing remediation strategies, and validating compliance posture.

### 2. Problem Statement
### What's the Problem?
Many cloud practitioners can deploy AWS infrastructure, but lack practical experience in **cloud security operations**. There is a significant gap between simply running cloud resources and securing them properly. Organizations often struggle with:
- Detecting common misconfigurations early (public S3 buckets, over-privileged IAM roles, unencrypted data)
- Implementing centralized logging and threat detection
- Understanding compliance frameworks and their implementation
- Responding to and remediating security findings in real-time

### The Solution
This workshop creates a **complete security operations lab** by intentionally deploying vulnerable AWS infrastructure, then systematically hardening it. Participants experience:
- **The Vulnerable Baseline**: Common misconfigurations (public S3 buckets, wildcard IAM permissions, unencrypted resources)
- **Continuous Monitoring & Detection**: AWS CloudTrail, Amazon GuardDuty, and AWS Security Hub for centralized threat detection
- **Securing & Remediation**: Applying the Principle of Least Privilege and executing hands-on hardening steps
- **Audit & Validation**: Pre- and post-hardening compliance assessment using Security Hub

### Benefits and Learning Outcomes
Participants gain **practical cloud security operations experience** through:
- Hands-on vulnerability identification and remediation
- Understanding AWS native security services integration
- Compliance validation and security posture assessment
- Replicable security best practices for production environments
- Foundation for advanced cloud security roles (Cloud Security Engineer, SecOps specialist)

### 3. Solution Architecture
The workshop lab architecture follows a **complete security lifecycle** with 6 sequential steps:

1. **Enable Security Services**: Activate AWS CloudTrail, Amazon GuardDuty, and AWS Security Hub to establish centralized logging and threat detection before deploying any workload.
   - **AWS CloudTrail**: Logs all API activity across the AWS account
   - **Amazon GuardDuty**: Threat detection using ML and threat intelligence
   - **AWS Security Hub**: Centralizes security findings and compliance checks

2. **Deploy Insecure Baseline**: Intentionally create common cloud misconfigurations
   - Public S3 buckets with no encryption
   - Over-privileged IAM roles with wildcard permissions
   - EC2 instances exposed to the internet with unrestricted SSH access

3. **Test & Validation**: Observe how Security Hub and GuardDuty detect and flag the misconfigurations
   - Review generated security findings in Security Hub
   - Analyze threat detection alerts from GuardDuty
   - Document the pre-hardening compliance baseline

4. **Hardening & Remediation**: Systematically fix each vulnerability based on Security Hub recommendations
   - Apply the Principle of Least Privilege to IAM policies
   - Enable encryption for data at rest and in transit
   - Restrict network access using security groups and network ACLs
   - Enable MFA for user accounts

5. **Re-validation**: Confirm that findings transition from Failed to Passed and compliance score improves
   - Assess against **CIS AWS Foundations Benchmark**
   - Compare Security Hub compliance scores before and after hardening
   - Document remediation actions and outcomes

6. **Clean-up**: Remove all lab resources to avoid ongoing charges
   - Terminate EC2 instances and delete S3 buckets
   - Disable CloudTrail, GuardDuty, and Security Hub
   - Verify complete resource teardown

### AWS Services Used
- **AWS CloudTrail**: Centralized API logging and audit trail
- **Amazon GuardDuty**: Threat detection using ML and threat intelligence
- **AWS Security Hub**: Centralized security findings and compliance assessment
- **Amazon S3**: Storage for CloudTrail logs and potential vulnerable data
- **Amazon EC2**: Compute instances (with intentional misconfigurations initially)
- **AWS IAM**: Identity and access management (including over-privileged roles)
- **Amazon VPC**: Networking (with intentionally weak security controls initially)

### Workshop Components
- **Insecure Infrastructure**: Baseline AWS environment with known vulnerabilities
- **Monitoring Pipeline**: Integrated CloudTrail, GuardDuty, and Security Hub
- **Hardening Playbook**: Step-by-step technical execution guide
- **Compliance Assessment**: Pre- and post-hardening Security Hub reports

### 4. Technical Implementation
**Implementation Approach**
The workshop is structured in sequential steps designed to build progressive security knowledge:

**Step 1: Enable Security Services (Foundation Phase - Weeks 1-2)**
- Learn AWS fundamentals: global infrastructure, shared responsibility model, core services
- Master IAM, S3, VPC, and CloudTrail through hands-on practice
- Set up AWS Free Tier account, IAM users, CLI, and billing alerts

**Step 2: Planning (Planning Phase - Week 3)**
- Design the Insecure-by-Design project architecture
- Identify three core misconfiguration scenarios: public S3, over-privileged IAM, exposed EC2
- Define the project directory structure and module layout

**Step 3: Enable Security Services (Execution Phase - Week 4)**
- Enable AWS CloudTrail logging to S3 for centralized API audit
- Activate Amazon GuardDuty for threat detection
- Configure AWS Security Hub as the centralized security dashboard

**Step 4: Deploy Insecure Baseline & Test (Execution Phase - Week 4)**
- Provision basic AWS infrastructure with intentional misconfigurations
- Create over-privileged IAM roles and policies with wildcard permissions
- Enable public S3 buckets without encryption
- Set up EC2 instances with permissive security groups (SSH open to 0.0.0.0/0)
- Review generated security findings in Security Hub dashboard
- Deploy GuardDuty Tester to generate 50+ finding types
- Document the pre-hardening compliance baseline for later comparison

**Step 5: Hardening & Remediation (Execution Phase - Week 4-5)**
- Implement IAM least privilege (remove wildcards, scope permissions)
- Enable encryption on S3 buckets and EBS volumes
- Restrict EC2 security groups to required ports only
- Enable MFA for IAM users
- Implement VPC Flow Logs for network monitoring
- Address each finding from Security Hub systematically

**Step 6: Re-validation & Clean-up (Execution Phase - Week 5)**
- Review post-hardening Security Hub compliance scores
- Compare with pre-hardening baseline
- Confirm findings transition from Failed to Passed
- Document all remediation actions taken
- Terminate EC2 instances and delete S3 buckets
- Disable CloudTrail, GuardDuty, and Security Hub
- Verify complete resource teardown to avoid ongoing charges

**Technical Requirements**
- AWS Account with appropriate permissions (for controlled lab environment)
- Practical knowledge of AWS IAM, S3, EC2, VPC, CloudTrail, GuardDuty, and Security Hub
- Familiarity with AWS Management Console and AWS CLI
- Understanding of cloud security concepts (principle of least privilege, defense in depth, CIS benchmarks)
- Ability to read and interpret CloudTrail logs and Security Hub findings

### 5. Timeline & Milestones
**Project Timeline (8-Week Internship Program)**

The workshop was conducted within an 8-week FCAJ internship program, structured in five phases:

- **Foundation Phase (Weeks 1-2, Jun 15-27)**: AWS fundamentals learning — global infrastructure, shared responsibility model, core services (EC2, IAM, S3, VPC, CloudTrail). AWS account setup, CLI configuration, billing alerts, and hands-on practice labs.

- **Planning Phase (Week 3, Jul 1-4)**: Designed the Insecure-by-Design workshop architecture; identified three core misconfiguration scenarios (public S3 bucket, over-privileged IAM role with wildcard permissions, EC2 instance with unrestricted SSH); defined the project structure.

- **Execution Phase (Weeks 4-5, Jul 6-18)**: Full security lifecycle execution:
    - **Week 4 (Jul 6-10)**: Enabled CloudTrail, GuardDuty, and Security Hub; deployed vulnerable baseline infrastructure; ran test & validation with GuardDuty Tester (50+ findings); executed hardening & remediation.
    - **Week 5 (Jul 13-18)**: Re-validated compliance — all three CIS controls transitioned from FAILED to PASSED; cleaned up all lab resources; compiled project documentation.

- **Extension Phase (Weeks 6-7, Jul 20-Aug 1)**: Researched and published technical blogs on AWS Security Hub and the Amazon GuardDuty Tester; attended the GenAI-powered App-DB Modernization workshop by AWS.

- **Finalization Phase (Week 8, Aug 3-14)**: Finalized bilingual workshop documentation; compiled compliance comparison report with before/after evidence; completed GuardDuty findings categorization; submitted final internship report.

**Key Deliverables**
- Vulnerable baseline infrastructure documentation
- Pre-hardening Security Hub assessment report
- Step-by-step hardening playbook with technical commands
- Post-hardening Security Hub assessment report
- Compliance comparison and remediation summary

### 6. Budget Estimation
**AWS Services Cost Estimation (Actual Lab Execution)**

The lab resources were active for approximately **2 weeks** (Weeks 4-5), with most services covered by AWS Free Tier or trial periods:

**Service Breakdown**
- **AWS CloudTrail**: Free (1 trail included in AWS Free Tier, management events only)
- **Amazon GuardDuty**: Free (30-day free trial covered the entire active period)
- **AWS Security Hub**: Free (30-day free trial covered the entire active period)
- **Amazon S3**: ~$1-2 (CloudTrail log storage; minimal data)
- **Amazon EC2**: ~$3-5 (t3.micro instance, ~2 weeks runtime)
- **AWS IAM**: Free (identity and access management)
- **Amazon VPC**: Free (virtual private cloud)
- **GuardDuty Tester (CDK)**: Covered under existing Free Tier limits

**Total Actual Cost**: ~$4-7 USD (EC2 t3.micro + S3 storage for CloudTrail logs)

**Cost Optimization Summary**
- Active lab window was intentionally compressed into 2 weeks to minimize costs
- GuardDuty and Security Hub 30-day free trials fully covered the security monitoring period
- t3.micro instance was selected for cost efficiency (~$0.0104/hr)
- All resources were verified as terminated/disabled during Week 5 clean-up
- AWS Budgets alerts were configured at $50 and $75 as a safety net

**Post-Workshop Cost Considerations**
- Lab infrastructure was fully cleaned up after Week 5 — no ongoing charges
- CloudTrail logs for the internship period are retained in S3 (minimal cost, ~$1-2/month for storage)
- The lab design enables future re-deployment using the documented steps at minimal cost

### 7. Risk Assessment
#### Risk Matrix

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| AWS Account Compromise | High | Low | Use dedicated lab account, enable MFA, monitor with GuardDuty |
| Accidental Infrastructure Deletion | High | Medium | Use AWS Config for resource tracking, enable termination protection |
| Cost Overruns | Medium | Low | Set AWS Budgets alerts, monitor daily costs, use resource limits |
| Insufficient Time for Hardening | Medium | Medium | Pre-plan remediation steps, document procedures in advance |
| GuardDuty/Security Hub Overwhelming Findings | Low | High | Filter findings by severity, focus on critical/high first |

#### Mitigation Strategies
- **Account Security**: Use a dedicated AWS account for the lab, separate from production
- **Resource Management**: Tag all resources for easy identification and cleanup
- **Monitoring**: Enable AWS Cost Explorer and set budget alerts at $50 and $75
- **Documentation**: Create runbooks for each remediation step before workshop begins
- **Backup**: Document the vulnerable baseline state to allow re-creation if needed

#### Contingency Plans
- If finding volume is overwhelming: Filter Security Hub to show only critical findings first
- If time runs short: Prioritize remediation based on CIS benchmark critical controls
- If costs exceed budget: Terminate non-essential resources, archive logs to Glacier
- If AWS services become unavailable: Use pre-captured findings for analysis and remediation planning

### 8. Expected Outcomes

#### Technical Knowledge & Skills
- Practical hands-on experience with AWS security services (CloudTrail, GuardDuty, Security Hub)
- Understanding of security misconfiguration types and their impact
- Proficiency in implementing the Principle of Least Privilege
- Ability to read and act on security findings
- Experience with security compliance frameworks (CIS AWS Foundations Benchmark)

#### Tangible Deliverables
- Fully documented vulnerable baseline for lab reproduction
- Complete hardening playbook with step-by-step commands
- Pre- and post-hardening compliance assessment reports
- Visual comparison of security improvements
- Reusable hardening procedures for production environments

#### Career Impact
- Foundation for Cloud Security Engineer or SecOps roles
- Practical experience with enterprise security tools and workflows
- Understanding of real-world cloud security challenges and solutions
- Portfolio-ready project demonstrating security expertise
- Framework for future advanced security topics (threat modeling, incident response, compliance automation)

#### Long-term Value
- Reusable lab environment for training others in cloud security
- Documented best practices applicable to organizational infrastructure
- Framework for assessing and improving existing AWS environments
- Base infrastructure for advanced security projects (threat hunting, automation, policy as code)