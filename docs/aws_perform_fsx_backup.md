---
title: "Performing FSx Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_perform_fsx_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing FSx Backup


One backup policy can be used to process one or more FSx file systems either within one AWS account or within an entire AWS Organization. The scope of data that you can protect in an AWS account is limited by permissions of an IAM role that is specified in the backup policy settings, whereas the scope of data that you can protect in an AWS Organization is limited by permissions of an IAM role that is specified in the organization settings.

To schedule data protection tasks to run automatically,
[create backup policies](aws_policies_create_fsx.md)
. For each protected FSx file systems, you can also
[take a backup manually](aws_backup_manual_fsx.md)
when needed.

|  |
| --- |
| Important |
| Before you create an FSx backup policy, check the limitations and prerequisites described in section  [Before You Begin](aws_add_fsx_policy_byb.md) . |

Page updated 2026-03-18

