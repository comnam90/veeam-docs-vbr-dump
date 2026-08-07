---
title: "Redshift Clusters Backup Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_retention_backup_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Clusters Backup Retention


For Redshift backups, the backup appliance retains restore points for the period of time specified in [backup scheduling settings](aws_add_policy_schedule_retention_redshift.md).

During every successful backup session, the backup appliance creates a restore point and saves the date, time and applied retention settings in the restore point metadata. If the appliance detects that the period of time for which the restore point was stored exceeds the period specified in the retention settings, it automatically removes the restore point from the Redshift chain. You can also remove unnecessary Redshift clusters backups manually as described in section [Removing Redshift Backups](aws_backups_remove_redshift.md).

[![Redshift Backup Retention](images/aws_redshift_backup_retention.webp)](images/aws_redshift_backup_retention.webp "Redshift Backup Retention")

|  |
| --- |
| Note |
| Backup appliances do not apply retention policy to Redshift backups created manually. For learn how to remove them, see [Removing Redshift Clusters Backups Created Manually](aws_backups_remove_individual_redshift.md). |

Page updated 2026-05-15

