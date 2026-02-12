---
title: "Copying Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_backups_copy.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Copying Backups


With backup copy, you can create several instances of a backup and copy them to secondary (target) backup repositories for long-term storage. Target backup repositories can be located in the same site as the source backup repository or can be deployed off-site. Since the backup copy has the same format as the original backup, you can restore VM data directly from the backup copy in case a disaster strikes. For more information on the backup copy functionality, see section [Backup Copy](backup_copy.md).

To copy backups to a secondary backup repository, do the following:

1. Open the Home view.
2. In the inventory pane, select Jobs > Backup and click Backup Copy > Image-level backup on the ribbon.
3. Create a backup copy job as described in section [Creating Backup Copy Jobs](backup_copy_create.md).

Note that for backup copies, you can also use Veeam Cloud Connect repositories if a service provider is added to Veeam Backup & Replication.

|  |
| --- |
| Tip |
| Alternatively, you can create a copy of a backup without configuring a job as described in section [Copying Backups](copy_backup.md). |

[![Backup Copy Jobs](images/sch_backups_copy.webp)](images/sch_backups_copy.webp "Backup Copy Jobs")


