---
title : "Architecture"
date : 2026-06-26 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Architecture Diagram

The data flow and security detection pipeline for this workshop is as follows:

<div style="text-align: center; margin: 20px 0;">
  <a href="architecture.drawio" target="_blank">
    <img src="Screenshots/Architecture.drawio.png" alt="Architecture Diagram" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px;" />
  </a>
  <br />
  <em>
    <a href="architecture.drawio" target="_blank">Open in draw.io editor</a>
    &nbsp;|&nbsp;
    <a href="https://app.diagrams.net/?grid=0&pv=0&border=10&edit=_blank#create=%7B%22type%22%3A%20%22xml%22%2C%20%22compressed%22%3A%20true%2C%20%22data%22%3A%20%227Zrdb%2BI4EMD%2FlntA2ntolU9CH8NXr1L7cnS1u08nk5jEVxMjxymwf%2F2NHQcICT02RQtEoIpmxvbYmfll%2FEE69qBjj1dz2rGMd8xTwpKOPexYlnlvwDdocRKwkCRRrv76Or7ryQJ73LFHHcPv2IP5akYohqoxS0VeLeRoSVhuoGTW6t4bueW8tWXIP3sQEhRxNAchQXOc1%2FW%2FTUCe4CDjRKzh0udBTAQORMbxvonC0Hz1yNEifmEhpjUVimqcMXGweGtrgKn0DAnzEWmXdKzxr7c187YLxHEiDpj70OIfd3fSB8opA8qyUP5niUAkwRyuofiXB2XpECGalZyu7cuyVKypLuMsS0Ism5odu7%2BUsZgsUCBLl%2BB00MUCSMqLQ5TGm7qp4OwNDxhlXJmyTccb9f1NyTcSihhKIKZ9gIkWNROWYKmC26xrLPUTPT6zkMlPJTogA3qCBIj6lEQSQMHkIJGWKJ4JOQK4BeD7WUnD3lbzKmsPpZ1g4%2Ba8n4BRihYpmaqewbP9BSOJwHz0DsFNtW6Dv8CrgwyY9SDXR%2B8RszkWXD4L2qKjGVpra10tL7VDQfIKXYxJFOtue0VDlOaKaGP6WMKhjubpeHiFQMGbovULy0RKQlxG%2Bs%2BGHNsVjr%2Bmqht5I7v9foboXTCBwlkvwEFQB%2Fe05zquJABSWkjwlt16nA31%2BR%2Bcrd8E1CYrrcuA7QDlGDVAuefgaTSQxp%2BSVKAkwA3Zcao5cI5%2BwoSl7e8hk8ZoIS%2Fnq0hONPdomTr3HKcs4wF%2BCuRE1wcxvyrXwoFVxWg09EwV%2FQpGM%2FU5gssdTI7OO9bnMDG7dgmTurzTq1JS6H4rJRMYqtHPIAGIhoi4hxGZ2McRMs37r4Tf833T7F5b%2BG3HvJrwP%2Fkv8P03o00TRPfAIkkZPio7yL4rkR8ObccZXFvkXfPhaiKvlhSvHBHaMPLeR8tjbfh000MgrQpltTpLeKbr9a89TVi9C6blMUM8HGZqp9kElt7hSWLH9OlwiaTRUBptSWrZp8U1LnlRsT2W%2BCubNkTm4UB%2B2Td%2BOmhSbfmfGOy2lBvPumBuRmEEzvHLm2GFTrGdaQKSaVRIqlCDoedid8m4iFnEEkRHW22%2FvBve1nlm6iREKv%2FFQqx1gFEmWDn6eEXEd3n6cW90tfhjp2i40icjSlgXQgI%2Bz1u5hfhjt2zbTEnbdqHPOVuCOKUseHuNSZKrx4QWI0KyRgHkHp9SpmiKaR%2FiEKmbryNeH4OquH205wZnqwewdCIhEI%2Bw2NloNsCcY4oEeS93fzHQqt3VlyWBJ80ylDubHuKYZgXiF5JCEpuRKOPgApak56XavUG9D7XbSqjzPWMjiK0Ly8QPzg3afWi7LYBWLxZyXj%2B90zXtC8O2Uaq1WoStU8XWawG2arlQR%2B1plhDVw%2FxnFsmu0KL41fi2fDgX0m47kdaLhVNlYrcNmdhrEbbddmJbJjWn97NnoGb1t5I%2BjtE7YXJx7QOA65TcNnFnxdmr4txrAc4ldPXRxCnOaM2aH4GiiONIHUiodl00X6hwGJOAcfmu3A3wMwLeqwL%2BcEWAq2oH3k%2FUJg684qhKizcpi7czVQP1gqbS%2FAc%3D%22%7D" target="_blank">Open in diagrams.net editor</a>
  </em>
</div>

#### Architecture Flow Explanation

1. **Vulnerability Entry** - An attacker or user exploits misconfigurations on EC2, S3, or IAM (e.g., public S3 bucket, global SSH access, `*/*` IAM policy).
2. **Log Capture** - AWS CloudTrail records all API calls, including malicious or unauthorized actions.
3. **Threat Detection** - Amazon GuardDuty analyzes behavior and logs to detect threats and anomalies.
4. **Aggregation & Assessment** - AWS Security Hub aggregates findings from GuardDuty and automatically scores compliance against the CIS AWS Foundations Benchmark.

#### AWS Services Used

| Service | Role |
|---------|------|
| **AWS CloudTrail** | Centralized API logging and audit trail |
| **Amazon GuardDuty** | ML-powered threat detection |
| **AWS Security Hub** | Centralized security findings and compliance assessment |
| **Amazon S3** | Storage for CloudTrail logs and potentially vulnerable data |
| **Amazon EC2** | Compute instances (with intentional misconfigurations initially) |
| **AWS IAM** | Identity and access management (including over-privileged roles) |
