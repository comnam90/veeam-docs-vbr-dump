---
title: "Removing Backup from Disk"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_backup_delete.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Backup from Disk


If you want to delete records about backups from the Veeam Backup & Replication interface and configuration database and, additionally, delete backup files from the backup repository, you can use the Remove from disk operation.

|  |
| --- |
| NOTE |
| * You can use the Veeam Backup & Replication interface to remove backups created by Veeam Agent backup jobs on the Veeam backup repository or Veeam Cloud Connect repository. Backups created on a local drive of a protected computer or in a network shared folder are not displayed in the Veeam Backup & Replication interface. * If you delete a backup of a failover cluster node, backup of all nodes of this cluster will be deleted. |

You can remove an entire backup related to a Veeam Agent backup job or remove specific child backups — backups related to individual computers in the backup.

You can remove a Veeam Agent backup in one of the following ways:

* [Using Veeam Backup & Replication Console](#console)
* [Using Veeam Backup & Replication Web UI](#webui)

Removing Backup from Disk Using Veeam Backup & Replication Console

To remove a Veeam Agent backup from the backup repository:

1. Open the Home view.
2. In the inventory pane, click Backups.
3. In the working area, select and remove the necessary backup:

* To remove the entire backup related to the Veeam Agent backup job or policy, select the backup and click Remove from > Disk on the ribbon or right-click the backup and select Remove from > Disk.
* To remove a backup of a specific computer in the Veeam Agent backup job or policy, expand the parent backup, select the necessary computer and click Remove from > Disk on the ribbon or right-click the computer and select Remove from > Disk.

[![Delete Backup from Disk](images/agent_remove_from_disk.webp)](images/agent_remove_from_disk.webp "Delete Backup from Disk")

Removing Backup from Disk Using Veeam Backup & Replication Web UI

To remove a Veeam Agent backup from the backup repository in the Veeam Backup & Replication web UI:

1. In the management pane, click Backups.
2. Select and remove the necessary backup:

* To remove the entire backup related to the Veeam Agent backup job or policy, select the check box next to the backup and click Delete on the toolbar. Alternatively, right-click the backup and select Delete.
* To remove a backup of a specific computer in the Veeam Agent backup job or policy, expand the parent backup, select the check box next to the necessary computer and click Delete on the toolbar. Alternatively, right-click the computer and select Delete.

[![Delete Backup from Disk](images/agent_remove_from_disk_web.webp)](images/agent_remove_from_disk_web.webp "Delete Backup from Disk")

Page updated 2026-07-20

