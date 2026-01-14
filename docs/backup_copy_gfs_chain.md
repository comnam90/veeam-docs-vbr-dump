---
title: "Backup Chain for GFS Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_gfs_chain.html"
last_updated: "8/31/2025"
product_version: "13.0.1.1071"
---

# Backup Chain for GFS Backups

In this article

GFS retention creates yearly, monthly and weekly full backups and functions in a combination with the short-term retention. Short-term retention policy cannot delete or merge these GFS full backups. Veeam Backup & Replication removes GFS backups only after the specified retention period for yearly/monthly/weekly backup is exceeded. Thus, the backup chain may contain more restore points than specified in the short-term retention policy.

When you enable the GFS retention, Veeam Backup & Replication no longer merges increments to full backups because GFS full backups cannot be modified. Thus, the short-term retention policy counts retention points only in the active backup chain not in the whole combination of backup chains.

|  |
| --- |
| Note |
| Veeam Backup & Replication removes GFS backup files only during running backup copy job sessions. This means that if the backup copy job does not run on the expected retention date, Veeam Backup & Replication will remove the GFS backup file later during the next job session. |

Multiple GFS Flags

If you schedule a monthly or yearly full backup on the same day when the weekly full backup is scheduled, Veeam Backup & Replication creates only one archive full backup. The created backup will be marked at the same time as weekly, monthly and yearly GFS backup. In the Veeam Backup & Replication console, you will see all GFS flags assigned to the backup.

The full backup can be marked as weekly, monthly and yearly. When transforming weekly, monthly and yearly backup chains, Veeam Backup & Replication checks flags set for the full backup file. If the full backup file belongs to some other retention policy tier and must be retained in the target backup repository, such backup file will not be removed.

Checking Which Restore Point Has GFS Flag

To check whether a restore point has a GFS flag, you can open the backup properties in the Veeam Backup & Replication console. Weekly, monthly, yearly backups have "W", "M" and "Y" flag in the Retention column. For instructions, see [Viewing Backup Properties](view_backup_copy_properties.md).

[![Backup Chain for GFS Backups](images/backup_copy_properties.webp)](images/backup_copy_properties.webp)

Page updated 8/31/2025

Page content applies to build 13.0.1.1071
