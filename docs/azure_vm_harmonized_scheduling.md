---
title: "Enabling Harmonized Scheduling"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_harmonized_scheduling.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Enabling Harmonized Scheduling


When you combine multiple types of schedules, Veeam Backup for Microsoft Azure applies the harmonization mechanism that allows you to leverage restore points for long-term retentions instead of taking a new restore point every time. The mechanism simplifies the backup schedule, optimizes the backup performance and reduces the cost of storing restore points.

With harmonized scheduling, Veeam Backup for Microsoft Azure can keep restore points created according to a daily, weekly or monthly schedule for longer periods of time:

* Cloud-native snapshots can be kept for weeks and months.
* Image-level backups can be kept for weeks, months and years.

For Veeam Backup for Microsoft Azure to use the harmonization mechanism, there must be specified at least 2 different schedules: one schedule will control the regular creation of restore points, while another schedule will control the process of retaining restore points. In terms of harmonized scheduling, Veeam Backup for Microsoft Azure re-uses restore points created according to a more-frequent schedule (daily, weekly or monthly) to achieve the desired retention for less-frequent schedules (weekly, monthly and yearly). Each restore point is marked with a flag of the related schedule type: the (D) flag is used to mark restore points created daily, (W) — weekly, (M) — monthly, and (Y) — yearly. Veeam Backup for Microsoft Azure uses these flags to control the retention period for the created restore points. Once a flag of a less-frequent schedule is assigned to a restore point, this restore point can no longer be removed — it is kept for the period defined in the retention settings. When the specified retention period is over, the flag is unassigned from the restore point. If the restore point does not have any other flags assigned, it is removed according to the retention settings of a more-frequent schedule.

|  |
| --- |
| Note |
| Restore points created according to a more-frequent schedule and less-frequent schedules compose a single backup or snapshot chain. This means that regardless of flags assigned to restore points, Veeam Backup for Microsoft Azure adds the restore points to the chain as described in sections [Backup Chain](azure_backup_chain_vm.md) and [Snapshot Chain](azure_snapshot_chain_vm.md). |

Consider the following example. You want a backup policy to create cloud-native snapshots of your critical workloads 3 times a day, to keep 3 daily snapshots in the snapshot chain, and also to retain one of the created snapshots for 2 weeks. In this case, you create 2 schedules when configuring the backup policy settings — daily and weekly:

1. In the daily scheduling settings, you select hours and days when snapshots will be created (for example, 7:00 AM, 9:00 AM, and 11:00 AM; Weekdays), and specify the number of daily restore points to retain (for example, 3).

Veeam Backup for Microsoft Azure will propagate these settings to the schedule with a lower frequency (which is the weekly schedule in our example).

[![Enabling Harmonized Scheduling](images/azure_policy_daily_harmonized_scheduling.webp)](images/azure_policy_daily_harmonized_scheduling.webp "Enabling Harmonized Scheduling")

1. In the weekly scheduling settings, you specify which one of the snapshots created by the daily schedule will be kept, and choose for how long you want to keep the selected snapshot.

For example, if you want to keep the daily restore point created at 7:00 AM on Monday for 2 weeks, you select 7:00 AM, Monday and specify 2 restore points to retain in the weekly schedule settings.

[![Enabling Harmonized Scheduling](images/azure_policy_weekly_harmonized_scheduling.webp)](images/azure_policy_weekly_harmonized_scheduling.webp "Enabling Harmonized Scheduling")

According to the specified scheduling settings, Veeam Backup for Microsoft Azure will create cloud-native snapshots in the following way:

1. On the first work day (Monday), a backup session will start at 7:00 AM to create the first restore point. The restore point will be marked with the (D) flag as it was created according to the daily schedule.

Since 7:00 AM, Monday is specified in the weekly scheduling settings, Veeam Backup for Microsoft Azure will assign the (W) flag to this restore point.

1. On the same day (Monday), after backup sessions run at 9:00 AM and 11:00 AM, the created restore points will be marked with the (D) flag.

[![Enabling Harmonized Scheduling](images/azure_retention_snapshots_daily_weekly.webp)](images/azure_retention_snapshots_daily_weekly.webp)

1. On the next work day (Tuesday), after a backup session runs at 7:00 AM, the created restore point will be marked with the (D) flag.

At the moment the backup session completes, the number of restore points with the (D) flag will exceed the retention limit specified in the daily scheduling settings. However, Veeam Backup for Microsoft Azure will not remove the earliest restore point (7:00 AM, Monday) with the (D) flag from the snapshot chain as this restore point is also marked with a flag of a less-frequent schedule. Instead, Veeam Backup for Microsoft Azure will unassign the (D) flag from the restore point. This restore point will be kept for the retention period specified in the weekly scheduling settings (that is, for 2 weeks).

[![Enabling Harmonized Scheduling](images/azure_retention_snapshots_daily_removed.webp)](images/azure_retention_snapshots_daily_removed.webp)

1. On the same day (Tuesday), after a backup session runs at 9:00 AM, the number of restore points with the (D) flag will exceed the retention limit once again. Veeam Backup for Microsoft Azure will remove from the snapshot chain the restore point created at 9:00 AM on Monday as no flags of a less-frequent schedule are assigned to this restore point.

[![Enabling Harmonized Scheduling](images/azure_retention_snapshots_daily_rp_removed.webp)](images/azure_retention_snapshots_daily_rp_removed.webp)

1. Veeam Backup for Microsoft Azure will continue creating restore points for the next week in the same way as described in steps 1–4.
2. On week 3, after a backup session runs at 7:00 AM on Monday, the number of kept restore points will exceed the retention limit. Veeam Backup for Microsoft Azure will unassign the (W) flag from the earliest kept restore point. Since no other flags are assigned to this restore point, Veeam Backup for Microsoft Azure will remove this restore point from the snapshot chain.

[![Enabling Harmonized Scheduling](images/azure_retention_snapshots_weekly_rp_removed.webp)](images/azure_retention_snapshots_weekly_rp_removed.webp)

Page updated 2025-08-20

