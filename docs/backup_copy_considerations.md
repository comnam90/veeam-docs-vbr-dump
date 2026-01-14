---
title: "Limitations and Considerations for GFS Retention Policy"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_considerations.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Limitations and Considerations for GFS Retention Policy

In this article

Before configuring the GFS retention policy for a backup copy job, consider the following limitations and considerations:

* [General Settings](#gen)
* [Periodic Copy Mode](#periodic)
* [Changes in GFS Retention After Upgrading from Veeam Backup & Replication 10 to version 12](#upgrade)

General Settings

Consider the following for general settings of a backup copy job:

* You cannot enable GFS retention settings if you use a backup repository with rotated drives as the target backup repository.
* [For yearly GFS cycle] If you enable only the yearly GFS cycle, you can encounter the case when there is one full backup and a large number of increments for the whole year. To avoid this case, it is recommended to enable an additional weekly GFS cycle. Weekly GFS cycle will update the backup chain every week which will allow removing excessive increment files.
* If for some reason the GFS synthetic full was not created in the scheduled day, Veeam Backup & Replication will create the synthetic GFS full after the next run of the backup copy job.
* If it is the day when the GFS full backup must be created and there were no new backup files since the last run of the backup copy, Veeam Backup & Replication will create the GFS full backup from the latest available backup chain.
* GFS full backups cannot be merged or deleted by short-term retention. However, regular (R) full backups can be merged and removed by short-term retention if GFS is disabled.
* [For [immediate copy mode](backup_copy_modes.md)] If the backup copy job was not run when the GFS full backup must be created, the GFS full backup will not be created on this day.

Periodic Copy Mode

If you want to use the [periodic copy mode](backup_copy_modes.md), consider the following:

* If Veeam Backup & Replication does not manage to transfer the restore point according to backup copy schedule, Veeam Backup & Replication will finalize the transfer anyway.
* Veeam Backup & Replication creates a GFS full backup even if the GFS full backup creation is scheduled when the backup copy scheduled run is not finished. On the day when the GFS full backup must be created, Veeam Backup & Replication shows a warning that the current backup copy scheduled run will be completed. The way Veeam Backup & Replication behaves further depends on the selected backup copy GFS method:

* In case of the synthetic full method, Veeam Backup & Replication first copies data for an incremental backup from the source backup repository and then, on the target backup repository, synthesizes the GFS full backup using this data and data of the already stored backup files.
* In case of the active full method, Veeam Backup & Replication copies data for the GFS full backup from the source backup repository and creates the GFS full backup on the target backup repository.

Changes in GFS Retention After Upgrading from Veeam Backup & Replication 10 to version 12

In Veeam Backup & Replication version 12, the backup copy GFS retention settings are different from the settings in version 10.

|  |
| --- |
| Important |
| If you run an upgrade from version 10 to version 12 when the GFS retention policy is disabled, Veeam Backup & Replication will delete all GFS storage repositories created before. |

If you upgrade to Veeam Backup & Replication 12, all GFS retention settings of existing backup copy jobs are automatically switched to the new format with minimal changes:

* Weekly GFS retention: If in version 10 the GFS setting was to keep 5 weekly backups, in version 12 the setting is changed to keep weekly backups for 5 weeks.
* Monthly GFS retention: If in version 10 the monthly GFS schedule was set to a period between the 1st Monday and 2nd Sunday, in version 12 the monthly GFS settings is changed to First week.

If the monthly GFS schedule was set to a period between the 3rd Monday and last Sunday, in version 12 the monthly GFS settings is changed to Last week.

* Yearly GFS retention: If the yearly GFS schedule was set to a certain day of the month, in version 12 the schedule is set to the first day of the specified month.

If in version 10 the yearly GFS schedule was set to the first-fourth Monday-Sunday of the year, in version 12 the schedule is changed to the first day of January.

If the yearly GFS schedule was set to the last Monday-Sunday of the year, in version 12 the schedule is set to the first day of December.

* Quarterly GFS retention: Since Veeam Backup & Replication version 11, quarterly GFS retention policy option is deprecated.

If in version 10 the quarterly GFS policy was enabled, in version 12 three additional months are added to the monthly GFS policy to compensate the quarterly full backups.

If in version 10, the GFS policy was set to X monthly backups and Y quarterly backups. Then, in version 12, the retention policy is switched to store monthly backups for (X + 3Y) months.

|  |
| --- |
| Important |
| [For synthetic method] Before the upgrade to Veeam Backup & Replication 12 or later, make sure that all GFS candidates (incremental restore points created on days when GFS was scheduled and that are expected to be transformed into full GFS restore points) are already transformed into GFS restore points. To force the backup copy job to transform all GFS candidates, you can temporarily decrease the short-term retention to a value less than the number of restore points between the latest restore point and the most recent GFS candidate and then wait till all the candidates are transformed.  Before Veeam Backup & Replication version 11, Veeam Backup & Replication created GFS candidates on days when GFS was scheduled and only then transformed them into full GFS restore points according to the short-term retention. For more information on how restore points were transformed, see [Synthetic Weekly Full Backups](https://helpcenter.veeam.com/archive/backup/100/vsphere/backup_copy_weekly_synthetic.html). Starting from Veeam Backup & Replication version 11, Veeam Backup & Replication creates GFS restore points according to a new schedule and creates them right on the scheduled days. After the upgrade, Veeam Backup & Replication no longer transforms previous GFS candidates into full GFS restore points. This means, that all GFS candidates lose their GFS status, they become regular incremental restore points and are deleted according to the short-term retention policy. |

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
