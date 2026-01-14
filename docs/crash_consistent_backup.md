---
title: "Crash-Consistent Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/crash_consistent_backup.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Crash-Consistent Backup

In this article

Crash-consistent backup is a proprietary Veeam method of creating crash-consistent VM images. A crash-consistent image can be compared to the state of a VM that has been manually reset. Unlike an offline backup, crash-consistent backup does not require any VM downtime.

|  |
| --- |
| Important |
| Crash-consistent backup does not preserve the data integrity of open files of transactional applications in the VM guest OS. This may result in data loss. |

Crash-consistent backup of VMs on Microsoft Hyper-V 2016 and later versions relies on standard checkpoints and works in the following way:

1. Veeam Backup & Replication requests a standard checkpoint of a specific VM.
2. Further activities depend on the backup mode:

+ In on-host backup mode, Veeam Backup & Replication reads data from VM disks in read-only state. After the VM processing is complete, the standard checkpoint is merged with the original VM.
+ In off-host backup mode, the Microsoft Hyper-V host VSS provider takes a snapshot of the volume on which VM disks are located.

The volume snapshot is mounted to the off-host backup proxy and presented to Veeam Backup & Replication. Veeam Backup & Replication reads VM data from the volume snapshot. After the backup job is complete, the volume snapshot and checkpoint are deleted.

![Crash-Consistent Backup](images/crash-consistent_backup_2016.webp)

Related Topics

* [Online Backup](online_backup.md)
* [On-Host Backup](onhost_backup.md)
* [Off-Host Backup](offhost_backup.md)

* [Creating Backup Jobs](backup_job_hv.md)

* [Creating Replication Jobs](replica_job_hv.md)

Page updated 8/11/2025

Page content applies to build 13.0.1.1071
