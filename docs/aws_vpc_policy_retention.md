---
title: "Step 4. Configure Retention Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_vpc_policy_retention.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Configure Retention Settings


At the Retention step of the wizard, specify retention settings for VPC configuration backups:

1. Click the Collect data link.
2. In the Daily retention window, specify how often the data will be backed up and for how long the backups will be stored.

If a restore point is older than the specified time limit, the backup appliance removes the restore point from the backup chain. For more information, see [VPC Configuration Backup Retention](aws_retention_backup_vpc.md).

|  |
| --- |
| Note |
| The backup appliance applies the retention settings configured for the VPC Configuration Backup policy both to VPC configuration backups stored in the appliance configuration database and to VPC configuration backups stored in the backup repository selected for the policy. For VPC configuration backups stored in backup repositories that are not specified in the VPC Configuration Backup policy settings, the backup appliance applies retention settings saved in the backup metadata. |

[![Editing VPC Configuration Backup Policy](images/aws_vpc_policy_retention.webp)](images/aws_vpc_policy_retention.webp "Editing VPC Configuration Backup Policy")

Page updated 2026-05-21

