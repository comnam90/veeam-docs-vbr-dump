---
title: "Using Backups Created on Crashed Backup Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replica_from_backup_another_srv.html"
last_updated: "1/22/2025"
product_version: "13.0.1.1071"
---

# Using Backups Created on Crashed Backup Server


There may be a situation when you created backups on one backup server, the server crashed and you want to use these backups for replica from backup on another backup server.

Veeam Backup & Replication considers backups created on other backup servers as imported backups. Replica from backups cannot use imported backups, that is why you need to perform the following steps to use backups created on the crashed server:

1. Import the backups to the backup server where you create the replication job. You have several options:

* You can connect the repository where the backups are stored to the backup server and then rescan the repository.
* You can copy backups to a backup repository already added to the backup server and then rescan the repository.
* You can copy backups to a backup repository already added to the backup server. Then [edit repository settings](backup_repo_edit.md) and select the Search the repository for existing backups and import them automatically check box at the [Review](repository_review.md) step of the wizard.

1. Create a new backup job or a backup copy job and map the imported backups to it. For more information on how to map backups, see [Specify Backup Storage Settings](backup_job_storage_vm.md).

After you map a backup to a job, Veeam Backup & Replication stops considering the backup as imported.

1. Create a replication job. In the job settings, specify that you want to use backups as a data source and select the backup repository where the imported backups reside. For more information, see [Specify Data Source](replica_data_source_vm.md).

|  |
| --- |
| Important |
| Consider the following:   * The backup job or backup copy job to which you map the imported backup file must run periodically and produce new restore points. Otherwise, the replication job will have no data to retrieve and replicas will be in an outdated state. * No other running backup servers must use the imported backups. |


