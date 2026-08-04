---
title: "Step 5. Specify Policy Scheduling Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sql_backup_policy_schedule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Policy Scheduling Options


You can instruct the backup appliance to start the backup policy automatically according to a specific backup schedule. The backup schedule defines how often data of the Azure SQL databases added to the backup policy will be backed up.

To help you implement a comprehensive backup strategy, the backup appliance allows you to create schedules of the following types:

* [Daily](azure_sql_schedule_daily.md) — the backup policy will create restore points repeatedly throughout a day on specific days.
* [Weekly](azure_sql_schedule_weekly.md) — the backup policy will create restore points once a day on specific days.
* [Monthly](azure_sql_schedule_monthly.md) — the backup policy will create restore points once a month on a specific day.
* [Yearly](azure_sql_schedule_yearly.md) — the backup policy will create restore points once a year on a specific day.

Combining multiple schedule types together allows you to retain restore points for longer periods of time — for more information, see [Enabling Harmonized Scheduling](azure_sql_harmonized_scheduling.md). Combining multiple schedule types together also allows you to archive backups — for more information, see [Enabling Backup Archiving](azure_sql_backup_archiving.md).

Page updated 2026-07-01

