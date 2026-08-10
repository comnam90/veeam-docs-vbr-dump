---
title: "Enabling Backup Archiving"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_cosmos_db_backup_archiving.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Enabling Backup Archiving


When you combine multiple types of schedules, you can enable the archiving mechanism to instruct the backup appliance to store backed-up data in the low-cost, long-term Archive access tier. The mechanism is the most useful in the following cases:

* Your data retention policy requires that you keep rarely accessed data in an archive.
* You want to reduce data-at-rest costs and to save space in the high-cost, short-term Hot and Cool access tiers.

|  |
| --- |
| Note |
| Restoring from an archived backup is longer and more expensive than restoring from a regular backup as it is required to retrieve data from the archive repository. For more information, see [Retrieving Data From Archive](azure_retrieving_cosmos_db_data.md). |

With backup archiving, the backup appliance can retain backups created according to a daily, weekly or monthly schedule for longer periods of time:

* To enable monthly archiving, you must configure a daily or a weekly schedule (or both).
* To enable yearly archiving, you must configure a daily, a weekly or a monthly schedule (or all three).

For the backup appliance to use the archiving mechanism, there must be specified at least 2 different schedules: one schedule will control the regular creation of backups, while another schedule will control the process of copying backups to an archive repository. Backup chains created according to these two schedules will be completely different — for more information, see [Backup Chain](azure_backup_chain_cosmos_db.md) and [Archive Backup Chain](azure_archive_chain_cosmos_db.md).

|  |
| --- |
| Tip |
| Copying backups to archive repositories is supported only from standard repositories with the same encryption settings (that is, data encryption must be either enabled or disabled). For example, if you instruct Veeam Backup for Microsoft Azure to store daily backups in a standard repository with encryption enabled, and monthly backups in an archive repository with encryption disabled, Veeam Backup for Microsoft Azure will not be able to archive these daily backups. However, data in the selected repositories can be encrypted differently (using a password or an Azure Key Vault cryptographic key). |

Consider the following example. You want a backup policy to create backups of your critical workloads once a week, to keep the backed-up data in a standard repository for 3 weeks, and also to keep backups created once in 2 months in an archive repository for a year. In this case, you create 2 schedules when configuring the backup policy settings — weekly and monthly:

1. In the weekly scheduling settings, you do the following:

1. Specify hours and days when backups will be created (for example, 7:00 AM, Monday), and specify the number of days for which the backup appliance will retain backups (for example, 21 days).
2. Select a repository of the Hot or Cool access tier that will store regular backups.

The backup appliance will propagate these settings to the archive schedule (which is the monthly schedule in our example).

[![Enabling Cosmos DB Backup Archiving](images/azure_cosmos_db_backup_archiving_weekly.webp)](images/azure_cosmos_db_backup_archiving_weekly.webp "Enabling Cosmos DB Backup Archiving")

1. In the monthly scheduling settings, you do the following:

1. Specify when the backup appliance will create archive backups, and choose for how long you want to retain the created backups (for example, January, March, May, July, September, November, 12 months and First Monday).
2. Enable the archiving mechanism by selecting a repository of the Archive access tier that will store archived data.

Note that when you enable backup archiving, you become no longer able to create a schedule of the same frequency for regular backups. By design, these two functionalities are mutually exclusive.

|  |
| --- |
| Important |
| If you enable backup archiving, consider the following:   * It is recommended that you set the Keep backups for value to at least 6 months (or 180 days), since the minimum storage duration of the Archive access tier is 180 days. * If you select the On Day option, [harmonized scheduling](azure_sql_harmonized_scheduling.md) cannot be guaranteed. Plus, to support the On Day option, the backup appliance will require to create an additional temporary restore point if there are no other schedules planned to run on that day. However, the temporary restore point will be removed during the Backup Retention process from Microsoft Azure Storage in approximately 24 hours, to reduce unexpected infrastructure charges. |

[![Enabling Cosmos DB Backup Archiving](images/azure_cosmos_db_backup_archiving_monthly.webp)](images/azure_cosmos_db_backup_archiving_monthly.webp "Enabling Cosmos DB Backup Archiving")

According to the specified scheduling settings, the backup appliance will create image-level backups in the following way:

1. On the first Monday of February, a backup session will start at 7:00 AM to create the first restore point in the regular backup chain. The backup appliance will store this restore point as a full backup in the repository.
2. On the second and third Mondays of February, the backup appliance will create restore points at 7:00 AM and add them to the regular backup chain as incremental backups in the repository.

![Enabling Backup Archiving](images/azure_backup_archiving_rp_weekly.webp)

1. On the fourth Monday of February, the backup appliance will create a new restore point at 7:00 AM. By the moment the backup session completes, the earliest restore point in the regular backup chain will get older than the specified retention limit. That is why the backup appliance will rebuild the full backup and remove from the chain the restore point created on the first Monday.

For more information on how backup appliances transform regular backup chains, see [Cosmos DB Backup Retention](azure_cosmos_db_backup_retention.md).

![Enabling Backup Archiving](images/azure_backup_archiving_weekly_retention.webp)

1. On the first Monday of March, a backup session will start at 7:00 AM to create another restore point in the regular backup chain. At the same time, the earliest restore point in the regular backup chain will get older than the specified retention limit again. That is why the backup appliance will rebuild the full backup again and remove from the chain the restore point created on the second Monday.

After the backup session completes, an archive session will create a restore point with all data from the regular backup chain. The backup appliance will copy this restore point as a full archive backup to the archive repository.

![Enabling Backup Archiving](images/azure_backup_archiving_rp_monthly.webp)

1. Up to May, the backup appliance will continue adding new restore points to the regular backup chain and deleting outdated backups from the repository, according to the specified weekly scheduling settings.

On the first Monday of May, an archive session will create a restore point with only that data that has changed since the previous archive session in March. The backup appliance will copy this restore point as an incremental archive backup to the archive repository.

[![Backup Archiving Example](images/azure_backup_archiving_monthly_incr.webp)](images/azure_backup_archiving_monthly_incr.webp "Backup Archiving Example")

1. Up to the first Monday of February of the next year, the backup appliance will continue adding new restore points to the regular backup chain and deleting outdated backups from the backup repository, according to the specified weekly scheduling settings. The backup appliance will also continue adding new restore points to the archive backup chain, according to the specified monthly settings.

By the moment the archive session completes, the earliest restore point in the archive backup chain will get older than the specified retention limit. That is why the backup appliance will rebuild the full archive backup and remove from the chain the restore point created on the first Monday of March of the previous year.

![Enabling Backup Archiving](images/azure_backup_archiving_monthly_retention.webp)

Page updated 2026-07-01

