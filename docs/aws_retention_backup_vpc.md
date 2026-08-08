---
title: "VPC Configuration Backup Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_retention_backup_vpc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VPC Configuration Backup Retention


For VPC configuration backups, the backup appliance retains restore points for the period of time specified in [backup retention settings](aws_vpc_policy_retention.md).

During every successful backup session, the backup appliance creates a restore point and saves the date, time and the applied retention settings in the restore point metadata. If the appliance detects that the period of time for which the restore point was stored exceeds the period specified in the retention settings, it automatically removes the restore point from the VPC configuration backup chain. You can also remove unnecessary VPC configuration backups manually as described in section [Removing VPC Configuration Backups](aws_backups_remove_vpc.md).

|  |
| --- |
| Note |
| Backup appliances apply the retention settings configured for the [VPC Configuration Backup policy](aws_vpc_policy_retention.md) both to VPC configuration backups stored in their databases and to those stored in the backup repositories selected for the policy. For VPC configuration backups stored in backup repositories that are not specified in the policy settings, backup appliances apply retention settings saved in the backup metadata. |

[![VPC Backup Retention](images/aws_vpc_backups_retention.webp)](images/aws_vpc_backups_retention.webp "VPC Backup Retention")

Page updated 2026-05-19

