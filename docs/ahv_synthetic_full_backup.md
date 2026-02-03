---
title: "Synthetic Full Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_synthetic_full_backup.html"
last_updated: "1/8/2026"
product_version: "13.0.1.1071"
---

# Synthetic Full Backup


In some situations, running active full backups periodically may not be an option. Active full backups are resource-intensive and consume considerable amount of network bandwidth. As an alternative, you can create synthetic full backups that also produce VBK files and contain data of the whole VM. However, while creating synthetic full backups, Veeam Backup & Replication connects to the cluster to retrieve only VM data that has changed since recent backup and processes it with the data that is already stored in the backup repository.

To create a synthetic full backup, Veeam Backup & Replication performs the following operations:

1. Veeam Backup & Replication creates a regular incremental backup and adds it to the backup chain.

![Synthetic Full Backup](images/vplugins_synthetic_fulls_how_1.webp)

1. Veeam Backup & Replication creates a new synthetic full backup using backup files that are already available in the backup chain, including the newly created incremental backup file.

![Synthetic Full Backup](images/vplugins_synthetic_fulls_how_2.webp)

1. Veeam Backup & Replication deletes the created incremental backup as its data is already incorporated in the synthetic full backup.

![Synthetic Full Backup](images/vplugins_synthetic_fulls_how_3.webp)

When creating a synthetic full backup, Veeam Backup & Replication starts a new backup chain for the VM. All further created incremental backups use the latest full backup file as a new starting point. The old full backup file from the old backup chain remains on disk until it is automatically deleted according to the retention policy.

Veeam Backup & Replication triggers a backup job to create a synthetic full backup even if a regular backup session is not scheduled on this day. For example, if you schedule the backup job to run at 12:00 AM Sunday through Friday, and schedule synthetic full backup to be created on Saturday, Veeam Backup & Replication will start a backup job session that will produce a synthetic full backup at 12:00 AM on Saturday.

If the backup job is not scheduled or is disabled, Veeam Backup & Replication will not perform synthetic full backup automatically. If a regular backup session and a synthetic full backup session are scheduled on the same day, Veeam Backup & Replication will produce a synthetic full backup only. However, if you run the backup job again on the same day manually, Veeam Backup & Replication will perform incremental backup in a regular manner.

Related Topics

[Creating Backup Jobs](ahv_backup_job_vbr_advanced.md)


