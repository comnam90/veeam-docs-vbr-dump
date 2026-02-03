---
title: "Retention Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_retention_policies.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Retention Policies


Backups created by jobs are not kept forever — they are removed according to retention policy settings specified while creating the jobs as described in section [Creating Backup Jobs](ovirt_backup_job_create.md).

Restore points in the backup chain are stored only for the allowed period of time (in days). If a restore point is older than the specified time limit, Veeam Backup & Replication removes it from the backup chain. To learn how Veeam Backup & Replication applies retention policies to forever forward incremental and forward incremental backup chains, see [Backup Retention](ovirt_backup_retention.md).

|  |
| --- |
| Note |
| Previous versions of Veeam Plug-in for oVirt KVM also had a retention policy setting that was based on the number of restore points. For this setting, if the number of allowed restore points was exceeded, Veeam Plug-in for oVirt KVM removed the earliest restore point from the chain. This functionality is now deprecated. All backup jobs created using the previous version of Veeam Plug-in for oVirt KVM will be processed according to their existing retention settings, but you will not be able to clone them or create new jobs with retention policy settings based on number of restore points. |


