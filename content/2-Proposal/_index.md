---
title: "Proposal"
date: 2026-06-26
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

In this section, you need to summarize the contents of the workshop that you **plan** to conduct.

# AWS Security Operations & Hardening Lab
## Insecure-by-Design to Managed Remediation

### 1. Executive Summary
The AWS Security Operations & Hardening lab approaches AWS Cloud through the lens of a **Cloud Security Engineer**, rather than simply deploying functioning resources. The core objective is to deploy a controlled, intentionally vulnerable cloud environment ("Insecure-by-Design"), monitor it using AWS native security services, and systematically harden it to meet enterprise security benchmarks such as the **CIS AWS Foundations Benchmark**. This hands-on workshop demonstrates the complete security lifecycle: from identifying misconfigurations, detecting threats in real-time, executing remediation strategies, and validating compliance posture.

### 2. Problem Statement
### What’s the Problem?
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

**Step 1: Enable Security Services (Week 1)**
- Enable AWS CloudTrail logging to S3 for centralized API audit
- Activate Amazon GuardDuty for threat detection
- Configure AWS Security Hub as the centralized security dashboard

**Step 2: Deploy Insecure Baseline (Week 1-2)**
- Provision basic AWS infrastructure with intentional misconfigurations
- Create over-privileged IAM roles and policies with wildcard permissions
- Enable public S3 buckets without encryption
- Set up EC2 instances with permissive security groups (SSH open to 0.0.0.0/0)
- Document the vulnerable state for later comparison

**Step 3: Test & Validation (Week 2)**
- Review generated security findings in Security Hub dashboard
- Analyze threat detection alerts from GuardDuty
- Document the pre-hardening compliance baseline and Security Hub score
- Capture evidence of misconfigurations for comparison

**Step 4: Hardening & Remediation (Week 3-4)**
- Implement IAM least privilege (remove wildcards, scope permissions)
- Enable encryption on S3 buckets and EBS volumes
- Restrict EC2 security groups to required ports only
- Enable MFA for IAM users
- Implement VPC Flow Logs for network monitoring
- Address each finding from Security Hub systematically

**Step 5: Re-validation (Week 4)**
- Review post-hardening Security Hub compliance scores
- Compare with pre-hardening baseline
- Confirm findings transition from Failed to Passed
- Document all remediation actions taken

**Step 6: Clean-up (Week 5)**
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
**Project Timeline**
- **Pre-Workshop (Week 0)**: Research cloud security concepts and CIS benchmark requirements
- **Workshop Execution (Weeks 1-5)**: 
    - Week 1: Enable security services (CloudTrail, GuardDuty, Security Hub)
    - Week 1-2: Deploy vulnerable baseline and run test & validation
    - Week 3-4: Execute hardening and remediation
    - Week 4: Re-validation of compliance scores
    - Week 5: Clean-up all lab resources
- **Post-Workshop**: Ongoing lab access for review and additional scenarios (up to 12 weeks)

**Key Deliverables**
- Vulnerable baseline infrastructure documentation
- Pre-hardening Security Hub assessment report
- Step-by-step hardening playbook with technical commands
- Post-hardening Security Hub assessment report
- Compliance comparison and remediation summary

### 6. Budget Estimation
**AWS Services Cost Estimation (Lab Execution)**

The following services will be utilized during the 5-week workshop:

**Service Breakdown**
- **AWS CloudTrail**: ~$2.50 (logging API calls across 5 weeks)
- **Amazon GuardDuty**: ~$30-40 (threat detection for 5 weeks, ~$6-8/week)
- **AWS Security Hub**: ~$30-40 (centralized findings, ~$6-8/week)
- **Amazon S3**: ~$1-2 (CloudTrail and log storage)
- **Amazon EC2**: ~$5-10 (small instances for 5 weeks)
- **AWS IAM**: Free (identity and access management)
- **Amazon VPC**: Free (virtual private cloud)

**Total Estimated Cost**: $70-90 USD for the complete 5-week lab

**Cost Optimization Notes**
- Lab resources are intentionally minimal to keep costs low
- CloudTrail and GuardDuty are essential for the learning objectives
- Resources can be terminated immediately after validation phase
- AWS Free Tier coverage may reduce or eliminate actual costs

**Post-Workshop Considerations**
- Lab infrastructure should be cleaned up after completion to prevent ongoing charges
- CloudTrail logs can be archived to Glacier for long-term retention at minimal cost
- Security Hub can be suspended until future security assessments are needed

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