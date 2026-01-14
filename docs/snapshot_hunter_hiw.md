---
title: "How Snapshot Hunter Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/snapshot_hunter_hiw.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# How Snapshot Hunter Works

In this article

A temporary snapshot of the VM is taken and then removed during every backup or replication job session. To remove the snapshot, Veeam Backup & Replication triggers the VMware snapshot consolidation mechanism that includes two steps:

1. VMware vSphere removes the snapshot from the VM snapshots list.
2. VMware vSphere consolidates the data written to the delta file with the VM disks.

The problem occurs when the snapshot was removed successfully, but the consolidation failed. This may happen, for example, if the files appear to be locked when VMware vSphere attempts to consolidate the snapshot files. In this case, the files remain on the datastore.

The Snapshot Hunter is started as a separate process scheduled within every job session. The discovery of phantom snapshots does not affect the job. If the phantom snapshots are discovered, the Veeam Backup Service schedules the snapshot consolidation, and the job runs normally.

Veeam Backup & Replication checks the datastore to discover orphaned snapshot files. To consolidate these files with the VM disks, Veeam Backup & Replication calls a consolidation algorithm. The algorithm consists of three steps, each representing a VMware method.

1. VMware Consolidate method

As a first attempt, Veeam Backup & Replication calls the VMware Snapshot Consolidate method. This method is the same mechanism that VMware vSphere uses for VMs with the Needs Consolidation status.

1. Hard consolidation without quiesce

If the first attempt fails, Veeam Backup & Replication creates a new snapshot and calls the VMware Delete all snapshots method. As a result, all VM snapshots and associated files are deleted. The snapshot is taken without quiescing the VM.

1. Hard consolidation with quiesce

If the snapshot deletion still fails, Veeam Backup & Replication implies another VMware method that creates a quiesced snapshot and then removes all VM snapshots.

|  |
| --- |
| Note |
| Hard consolidation without quiesce and hard consolidation with quiesce are performed only if the VM does not have any user snapshots. In case there are one or more user snapshots, these steps will not be performed. |

The 3-steps consolidation procedure is launched up to 4 times with a 4-hour interval.

In case all four attempts fail, Veeam Backup & Replication sends an e-mail notification informing that the user needs to manually troubleshoot the problem. Note that you need to have the global email notifications option enabled. For more information, see [Specifying Email Notification Settings](email_notification_settings.md).

The Snapshot Hunter considers the backup window set for the job. If any of the attempts does not fit the backup window, Veeam Backup & Replication will not perform the consolidation and send the e-mail notification.

To view information on the Snapshot Hunter sessions, in the Veeam Backup & Replication console, open the History view and select System in the [inventory pane](vbr_ui.md).

In case no consolidation attempt could fit the backup window, the warning appears in the job statistics.

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
