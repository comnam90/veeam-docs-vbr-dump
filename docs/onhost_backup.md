---
title: "On-Host Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/onhost_backup.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# On-Host Backup


During on-host backup, VM data is processed on the source Microsoft Hyper-V host where VMs that you want to back up or replicate reside. All processing operations are performed directly on the source host, which performs the role of the backup proxy. For this reason, on-host backup may result in high CPU usage and network overhead on the host system. For more information about the backup of VMs registered on Microsoft Hyper-V 2016 and later versions, see [Online Backup](online_backup.md) and [Crash-Consistent Backup](crash_consistent_backup.md).

The on-host backup process is performed in the following way:

1. Veeam Backup & Replication triggers a snapshot of the necessary volume.
2. Veeam Data Mover on the host uses the created volume snapshot to retrieve VM data; it processes the VM data and copies it to the destination.
3. After the backup process is complete, the volume snapshot is deleted.

![On-Host Backup](images/onhost_backup_mode.webp)

Related Topics

* [Off-Host Backup](offhost_backup.md)

* [Creating Backup Jobs](backup_job_hv.md)

* [Creating Replication Jobs](replica_job_hv.md)


