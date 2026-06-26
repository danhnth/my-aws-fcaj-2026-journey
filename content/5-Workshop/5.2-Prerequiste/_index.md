---
title : "Prerequisites"
date : 2024-01-01 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

#### Prerequisites

Before starting this workshop, ensure you have the following:

1. **AWS Account** — A valid AWS account with administrative access. A new or sandbox AWS Free Tier account is recommended to avoid impacting production workloads.

2. **AdministratorAccess Permission** — Your IAM user or role must have the `AdministratorAccess` managed policy (or equivalent permissions) to enable and configure security services.

3. **AWS CLI** — The AWS Command Line Interface installed and configured on your local machine. [Installation guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

4. **Default Region** — Set your default region to **Singapore (ap-southeast-1)** for consistency with this workshop.

   ```bash
   aws configure set region ap-southeast-1
   ```

5. **Basic AWS Knowledge** — Familiarity with the AWS Management Console, IAM, S3, EC2, and basic networking concepts is helpful but not required.