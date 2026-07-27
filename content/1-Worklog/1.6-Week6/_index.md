---
title: "Week 6 Worklog"
date: 2026-07-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Research and understand Amazon EKS Pod Identity and the Session Policies feature.
* Write a technical blog explaining how Session Policies can narrow IAM permissions for individual pods.
* Publish the blog on the AWS Study Group community and share knowledge with fellow learners.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (20/07) | - Research Amazon EKS Pod Identity architecture <br>&emsp; + Understand how Pod Identity maps IAM roles to Kubernetes service accounts <br>&emsp; + Compare with the traditional IRSA (IAM Roles for Service Accounts) approach <br> - Set up a test EKS cluster (if needed) for hands-on exploration | 20/07/2026 | 20/07/2026 | <https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html> |
| Tue (21/07) | - Deep-dive into Session Policies for EKS Pod Identity <br>&emsp; + Learn how session policies further restrict permissions at the pod level <br>&emsp; + Understand use cases: multi-tenant workloads, least-privilege per pod <br>&emsp; + Review example IAM session policy documents | 21/07/2026 | 21/07/2026 | <https://docs.aws.amazon.com/eks/latest/userguide/eks-pod-identity-session-policies.html> |
| Wed (22/07) | - Write the first draft of the technical blog <br>&emsp; + Structure: introduction, problem statement, solution overview, step-by-step guide <br>&emsp; + Include code snippets for IAM roles, service accounts, and session policies <br>&emsp; + Add architecture diagrams explaining the flow | 22/07/2026 | 23/07/2026 | |
| Thu (23/07) | - Review and refine the blog draft <br>&emsp; + Verify technical accuracy of all AWS CLI commands and IAM policy examples <br>&emsp; + Add screenshots of EKS console and IAM configurations <br>&emsp; + Proofread for clarity and correct English | 23/07/2026 | 24/07/2026 | |
| Fri (24/07) | - Final review and publish the blog on AWS Study Group <br>&emsp; + Format the post for the community platform <br>&emsp; + Add tags and category for discoverability <br>&emsp; + Share the published link with the FCAJ cohort for feedback | 24/07/2026 | 24/07/2026 | <https://awsstudygroup.com/> |
| Sat (25/07) | - **Practice:** <br>&emsp; + Document the key technical insights gained during the blog writing process <br>&emsp; + Reflect on how session policies compare to other IAM isolation mechanisms <br> - Review Week 6 progress and prepare for the Week 7 workshop | 25/07/2026 | 25/07/2026 | |

### Week 6 Achievements:

* Gained a thorough understanding of Amazon EKS Pod Identity - how it maps IAM roles to Kubernetes service accounts at the pod level, and how it simplifies the credential management pipeline compared to the traditional IRSA approach.

* Mastered the Session Policies feature for EKS Pod Identity:
  * Understand how session policies act as a runtime permission boundary, further narrowing the IAM role's permissions for individual pods
  * Identified key use cases: multi-tenant EKS clusters where different pods need different permission levels, and scenarios requiring dynamic, fine-grained access control
  * Created example session policy documents demonstrating read-only vs read-write access patterns

* Wrote and published a technical blog on the topic, covering:
  * The motivation for pod-level IAM isolation in Kubernetes
  * A step-by-step guide to setting up EKS Pod Identity with session policies
  * Real-world code examples and architecture diagrams
  * A comparison between IRSA and the new Pod Identity approach

* Published the blog on the AWS Study Group community platform and shared it with the FCAJ cohort, receiving positive feedback from peers and mentors.

* Strengthened technical writing skills - learned to explain complex AWS security concepts in an accessible way for the cloud community.
