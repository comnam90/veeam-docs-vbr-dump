---
title: "Retention Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_retention_policy.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Retention Policies


Image-level backups created by jobs are not kept forever — they are removed according to retention policy settings specified while creating the jobs as described in section [Creating Backup Jobs](sangfor_backup_job_create.md).

Restore points in the backup chain are stored only for the allowed period of time (in days). If a restore point is older than the specified time limit, Veeam Backup & Replication removes it from the backup chain. To learn how Veeam Backup & Replication applies retention policies to forever forward incremental and forward incremental backup chains, see [Backup Retention](sangfor_backup_retention.md).

Page updated 2026-04-14

