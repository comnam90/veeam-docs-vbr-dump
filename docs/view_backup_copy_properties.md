---
title: "Viewing Backup Properties"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/view_backup_copy_properties.html"
last_updated: "5/21/2025"
product_version: "13.0.1.1071"
---

# Viewing Backup Properties

In this article

You can view summary information about backups created by backup copy jobs. The summary information provides the following data: available restore points, date of restore points creation, compression and deduplication ratios, data size and backup size.

|  |
| --- |
| Note |
| Data Size represents the size of a backup file before compression and deduplication. Backup Size represents the size of a backup file after compression and deduplication. |

In the summary information, Veeam Backup & Replication displays data about restore points created by the short-term retention scheme and archive restore points created by the GFS retention scheme (if GFS retention is enabled). Archive restore points are marked with the following letters:

* R — full backups created with the short-term retention scheme or active full backups
* W — weekly backups
* M — monthly backups
* Y — yearly backups

In the summary information, you can also see the following icons:

| Icon | State |
| --- | --- |
| ![Viewing Backup Properties](images/icon_full.webp) | Full restore point |
| ![Viewing Backup Properties](images/icon_forward_incremental.webp) | Incremental restore point |
| ![Viewing Backup Properties](images/icon_reverse_incremental.webp) | Reverse incremental restore point |
| ![Viewing Backup Properties](images/icon_full_unavailable.webp) | Missing full restore point |
| ![Viewing Backup Properties](images/icon_forward_unavailable.webp) | Missing incremental restore point |

To view summary information for a backup copy:

1. Open the Home view.
2. In the inventory pane, select Backups > Disk (copy).
3. In the working area, right-click the backup copy and select Properties.

[![Viewing Backup Properties](images/backup_copy_properties.webp)](images/backup_copy_properties.webp)

Page updated 5/21/2025

Page content applies to build 13.0.1.1071
