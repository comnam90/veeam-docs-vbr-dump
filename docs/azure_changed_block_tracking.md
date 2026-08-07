---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_changed_block_tracking.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Changed Block Tracking


The changed block tracking (CBT) mechanism allows backup appliances to reduce the amount of data read from cloud-native snapshots, and to increase the speed and efficiency of incremental backups:

* During a full backup session, the backup appliance reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, the backup appliance reads only those data blocks that have changed since the previous backup session.

To detect unallocated and changed data blocks, CBT relies on [Azure Compute APIs](https://docs.microsoft.com/en-us/rest/api/azure/).

* During the first (full) backup session, the backup appliance creates a cloud-native snapshot of an Azure VM. The backup appliance sends API requests to access the content of the snapshot and to detect unallocated data blocks.
* During subsequent sessions, new cloud-native snapshots are created. The backup appliance sends API requests to access and to compare the content of the snapshot created during the previous backup session and the snapshot created during the current backup session. This allows the backup appliance to detect data blocks that have changed since the previous backup session.

|  |
| --- |
| Note |
| The CBT mechanism is optional for SLA-based backup policies. For more information, see [Temporary Restore Points](azure_temporary_restore_points.md#temporary_snapshots). |

To allow the CBT mechanism to be used when processing Azure VM data by a backup policy, the number of snapshots to keep in a snapshot chain must be enough to ensure that the cloud-native snapshot created during the previous backup session has not been removed from the chain by the retention policy before the next backup session runs. For more information on configuring snapshot retention settings, see [Creating Backup Policies](azure_vm_schedule_daily.md).

Consider the following example. You want a schedule-based backup policy to daily create both image-level backups and cloud-native snapshots: cloud-native snapshots must be created at 7:00 AM, 9:00 AM, 11:00 AM 1:00 PM, 3:00 PM and 5:00 PM; image-level backups must be created at 7:00 AM and 5:00 PM. In this case, you must set the Snapshots to keep value to minimum 5. Veeam Backup for Microsoft Azure will run the backup policy in the following way:

1. At 7:00 AM, a backup session will create a cloud-native snapshot, and then use this snapshot to create an image-level backup.
2. From 9:00 AM to 3:00 PM, backup sessions will create only cloud-native snapshots.
3. After a backup session runs at 5:00 PM, the first cloud-native snapshot (created at 7:00 AM) will still be present in the snapshot chain until the next backup session.

Page updated 2026-07-01

