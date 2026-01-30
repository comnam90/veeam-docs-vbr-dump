---
title: "Replica from Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replica_from_backup_hv.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Replica from Backup


Disaster recovery plans often require that you back up and replicate the same VM for disaster recovery (DR) and high availability (HA) purposes. As a rule, this doubles the workload on the virtual infrastructure: two VM snapshots need to be created independently from one another, and VM data need to be transferred from the production site twice.

To minimize the use of compute, storage and network resources, you can use the replica from backup option. You can use this option in both on-site and off-site replication scenarios.

When you perform replication from backup, Veeam Backup & Replication does not address hosts and storage in the production environment to read VM data. As a source of data, Veeam Backup & Replication uses a backup chain that already exists in a backup repository. As a result, Veeam Backup & Replication creates only one snapshot and transfers VM data only once. Veeam Backup & Replication retrieves VM data only while a backup or backup copy job is running. The replication job re-uses retrieved data to build VM replica restore points.

Differences between Seeding and Replica from Backup

Although replica from backup may resemble [replica seeding](replica_seeding_hv.md), there is difference between these options:

* Replica seeding uses a backup file only during the first run of a replication job. To further build VM replica restore points, the replication job addresses the production environment and reads VM data from the source storage.
* Replica from backup uses a backup chain in a backup repository as the only source of data. When building a new VM replica restore point, Veeam Backup & Replication always reads data from the latest restore point in the backup chain, either full or incremental. The backup chain in the backup repository may be created by a backup job or a backup copy job.

Requirements and Limitations for Replica from Backup

Consider the following requirements and limitations:

* You can perform replication only from backups of Microsoft Hyper-V virtual machines created with Veeam Backup & Replication.
* Replica from backup processes disks sequentially, not in parallel.
* Replica from backup can use the following backups only:

* Backups that backup jobs or backup copy jobs create. These jobs must be configured on the same backup server where you configure the replication job.
* Backups to which backup jobs or backup copy jobs are mapped. These jobs must be configured on the same backup server where you configure the replication job.

* The jobs mentioned in the previous list items must run periodically and produce new restore points. Otherwise, the replication job will have no data to retrieve and replicas will be in an outdated state.
* Replica from backup cannot use imported backups. However, there may be a situation when you need to use backups created on another backup server. In this case, use the instructions provided in [Using Backups Created on Crashed Backup Server](replica_from_backup_another_srv_hv.md). Note that the backup server from which you import backups must not operate anymore, otherwise replica from backup may behave in an unexpected way.

* [For backups stored on scale-out backup repositories] Replica from backup ignores backups stored in a tier other than the performance tier.

Related Topics

* [How Replica from Backup Works](replica_from_backup_hiw_hv.md)
* [Creating Replication Jobs](replica_job_hv.md)


