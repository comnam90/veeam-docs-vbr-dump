---
title: "Retention Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_retention_policy.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Retention Policies


Image-level backups created by jobs are not kept forever — they are removed according to retention policy specified while creating the jobs as described in section [Creating Backup Jobs](ahv_backup_job_create.md).

Restore points in the backup chain are stored only for the allowed period of time (in days). If a restore point is older than the specified time limit, Veeam Backup & Replication removes it from the backup chain. To learn how Veeam Backup & Replication applies retention policies to forever forward incremental and forward incremental backup chains, see [Backup Retention](ahv_retention_backups.md).


