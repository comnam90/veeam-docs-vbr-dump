---
title: "RDS Backup Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_retention_backup_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# RDS Backup Retention


The forever forward incremental backup method is not implemented for DB instances — during every backup session the backup appliance creates a full backup in the regular backup chain. If the appliance detects an outdated restore point in a backup repository, it removes this restore point from the backup chain.

Page updated 2026-05-15

