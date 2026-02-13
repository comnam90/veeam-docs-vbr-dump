---
title: "Retention Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_retention_policy.html"
last_updated: "2/5/2026"
product_version: "13.0.1.1071"
---

# Retention Policies


Backups created by jobs are not kept forever — they are removed according to retention policy settings specified while creating the jobs as described in section [Creating Backup Jobs](sch_backup_job_create.md).

Restore points in the backup chain can be stored only for the allowed period of time. If a restore point is older than the specified time limit, Veeam Plug-in for Scale Computing HyperCore removes it from the backup chain.

To learn how Veeam Plug-in for Scale Computing HyperCore applies retention policies to forever forward incremental and forward incremental backup chains, see [Backup Retention](sch_backup_retention.md).


