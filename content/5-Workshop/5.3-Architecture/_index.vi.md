---
title : "Kiến trúc"
date : 2026-06-26 
weight : 1
chapter : false
pre : " <b> 5.3. </b> "
---

#### Mô tả kiến trúc

[User/Attacker] ──(Cấu hình sai)──> [ EC2 / S3 Bucket / IAM Role ]
                                              │
                                        (Ghi nhận Log)
                                              ▼
                                       [ AWS CloudTrail ]
                                              │
                                        (Phân tích hành vi)
                                              ▼
                                      [ Amazon GuardDuty ]
                                              │
                                        (Tổng hợp & Chấm điểm)
                                              ▼
                                      [ AWS Security Hub ]