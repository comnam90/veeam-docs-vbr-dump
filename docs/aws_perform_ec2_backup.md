---
title: "Performing EC2 Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_perform_ec2_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing EC2 Backup


One backup policy can be used to process one or more instances either within one AWS account or within an entire AWS Organization. The scope of data that you can protect in an AWS account is limited by permissions of an IAM role that is specified in the backup policy settings, whereas the scope of data that you can protect in an AWS Organization is limited by permissions of an IAM role that is specified in the organization settings.

To schedule data protection tasks to run automatically, create backup policies. For each protected EC2 instance, you can also [take cloud-native snapshots manually](aws_snapshot_manual.md) when needed.

|  |
| --- |
| Important |
| Before you create an EC2 backup policy, check the limitations and prerequisites described in sections [Creating Schedule-Based EC2 Backup Policies](aws_add_schedule_based_policy_byb.md) and [Creating SLA-Based EC2 Backup Policies](aws_add_sla_based_policy_byb.md). |

Related Topics

[SLA-Based Backup Policies](aws_overview_ec2.md#policies)

Page updated 2026-05-21

