---
title: "Backup of VMs on Local Storage and CSV"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_process.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Backup of VMs on Local Storage and CSV


For backup of VMs on local storage and CSV (Cluster Shared Volumes), Veeam Backup & Replication uses the Microsoft VSS framework and Microsoft Hyper-V VSS components. Veeam Backup & Replication acts as a Microsoft VSS requestor and communicates with the Microsoft VSS framework. It obtains information about available Microsoft VSS components from Microsoft VSS, specifies which components Microsoft VSS must use, identifies the volumes where VM files are located, and triggers the Microsoft VSS coordinator to create volume snapshots.

Before a snapshot of a volume is created, VMs on the volume must be quiesced. There must be no incomplete transactions or open files. Veeam Backup & Replication uses two methods to prepare Microsoft Hyper-V VMs for backup:

* [Online backup](online_backup.md) (also known as Child VM Snapshot method) — native Microsoft Hyper-V mechanism that allows you to create an application-consistent image of running VMs without downtime.

* [Crash-consistent backup](crash_consistent_backup.md) — Veeam’s proprietary mechanism that allows you to create a crash-consistent VM backup. During crash-consistent backup, VMs are not brought to the saved state.

Whenever possible, Veeam Backup & Replication uses the online backup method to quiesce VMs. If online backup cannot be performed, Veeam Backup & Replication fails over to the crash-consistent backup.

|  |
| --- |
| Note |
| Veeam Backup & Replication does not fail over to the crash-consistent backup mode if you enable application-aware processing for a job and enable the Require successful processing option. In such a situation, if application-aware processing fails, Veeam Backup & Replication will terminate the job with the Error status. |

Related Topics

* [Backup Modes](backup_modes.md)
* [Creating Backup Jobs](backup_job_hv.md)
* [Creating Replication Jobs](replica_job_hv.md)


