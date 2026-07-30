---
title: "Blog 3"
date: 2026-07-22
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS Cloud Security & Compliance — Understanding Risk and Compliance on the Cloud

During my internship at AWS FCAJ, I've developed a strong interest in Cloud Security and have been exploring various AWS resources. I recently went through the **AWS Risk and Compliance** whitepaper, which lays out the fundamental framework for moving systems to the cloud properly.

## The Shared Responsibility Model

The core takeaway from this whitepaper is the **Shared Responsibility Model**. Many people mistakenly believe that moving everything to the cloud means AWS handles everything from A to Z.

In reality, AWS is only responsible for securing **the cloud infrastructure itself** — physical security at data centers, hardware, networking, and the virtualization layer. Security **inside** the cloud — your data, IAM permissions, operating systems, and firewall configurations — is entirely the customer's responsibility.

## Compliance Governance

The whitepaper also clarifies how AWS customers must proactively manage and ensure compliance within their own environments. A sound compliance governance process typically involves these steps:

1. **Understand your compliance requirements** by cross-referencing the AWS Shared Responsibility Model, AWS Security Documentation, and reports available on AWS Artifact.
2. **Design and implement controls** that meet the required standards under the shared responsibility model.
3. **Identify and document** any controls managed by third parties.
4. **Continuously audit and verify** that your security mechanisms are actually working as intended.

## What AWS Does on Their Side

On the flip side, to build customer trust, AWS integrates a wide range of risk management and compliance mechanisms into their platform — including automated tools and diverse security controls. Additionally, AWS undergoes regular **third-party audits** to maintain reputable certifications, ensuring the integrity of their control environment and directly benefiting their customers.

## Conclusion

Reading this whitepaper gave me a more practical perspective when designing and running labs on the cloud. Security isn't just about turning on scanning tools or writing code — it's about understanding the lines of responsibility and building continuous control processes to keep systems running safely.

## References

- [AWS Risk and Compliance Whitepaper](https://docs.aws.amazon.com/whitepapers/latest/aws-risk-and-compliance/welcome.html)

**Tags:** `#AWS` `#CloudSecurity` `#Compliance` `#SharedResponsibility` `#FCAJ` `#AWSStudyGroup`
