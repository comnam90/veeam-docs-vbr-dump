---
title: "Step 5. Configure Backup Target Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_target_settings_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Configure Backup Target Settings


By default, backup policies create only cloud-native snapshots of processed instances. At the Targets step of the wizard, you can enable the following additional data protection scenarios:

* [Instruct the backup appliance to replicate cloud-native snapshots to other AWS accounts or AWS Regions](aws_add_policy_target_settings_rds_replica.md).
* [Instruct the backup appliance to create image-level backups](aws_add_policy_target_settings_backups_rds.md).

|  |
| --- |
| Important |
| Creating image-level backups is supported for Microsoft SQL Server and PostgreSQL DB instances only. For the list of supported PostgreSQL versions, see [Protecting RDS Resources](aws_overview_rds.md#applications). |

Page updated 2026-05-21

