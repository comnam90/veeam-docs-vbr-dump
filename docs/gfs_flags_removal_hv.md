---
title: "Removal of GFS Flags"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/gfs_flags_removal_hv.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# Removal of GFS Flags

In this article

When configuring GFS retention policy settings, you can specify the retention period for each type of GFS flag. After the specified retention period exceeds, Veeam Backup & Replication removes GFS flags.

The date when Veeam Backup & Replication can remove the GFS flag is calculated by the following formulas:

* Weekly: date of GFS flag assignment + N \* 7 days
* Monthly: date of GFS flag assignment + N months + 1 day

When calculating the date of GFS flag assignment + N months, Veeam Backup & Replication increases the month ordinal number by N. If the calculated date does not exist, Veeam Backup & Replication uses the last day of the calculated month.

* Yearly: date of GFS flag assignment + N years + 1 day

Where N is the value specified in the Keep weekly/monthly/yearly full backups for field. For more information, see [Configure Long-Term Retention](backup_job_gfs_hv.md).

|  |
| --- |
| Note |
| Consider the following:   * Veeam Backup & Replication removes GFS flags during running backup job sessions. This means that if the backup job does not run on the calculated date, Veeam Backup & Replication will remove the GFS flag later during the next job session. * GFS flags can also be removed during the background GFS retention process. It detects backup files that have assigned GFS flags and removes flags with an expired retention period. For more information, see [Background GFS Retention](background_retention_job_hv.md). * After you change GFS retention policy settings, the date of GFS flag removal is recalculated for already created restore points. |

Consider the following example. At the beginning of January, you create a backup job whose GFS retention policy settings are configured to assign monthly GFS flags. You want to keep backup files with monthly flags for 1 month and set the value of the Keep monthly full backups for field to 1. Veeam Backup & Replication will perform the following steps to assign and remove the flags.

1. Veeam Backup & Replication will assign the monthly GFS flag on 1/31/2019.
2. To calculate the date when the monthly flag must be removed, the following formula is used: date of GFS flag assignment + 1 month. This means that the flag must be removed on 2/31/2019. However, this date does not exist since the last date of February is 2/28/2019. That is why Veeam Backup & Replication will remove the GFS flag on 3/1/2019 (which is 2/28/2019 + 1 day).

Page updated 2/11/2025

Page content applies to build 13.0.1.1071
