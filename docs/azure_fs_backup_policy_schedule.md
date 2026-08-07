---
title: "Step 4. Specify Policy Scheduling Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_fs_backup_policy_schedule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Specify Policy Scheduling Options


You can instruct the backup appliance to start the backup policy automatically according to a specific backup schedule. The backup schedule defines how often data stored in file systems added to the backup policy will be backed up.

To help you implement a comprehensive backup strategy, the backup appliance allows you to create schedules of the following types:

* [Daily](azure_fs_schedule_daily.md) — the backup policy will create restore points repeatedly throughout a day on specific days.
* [Weekly](azure_fs_schedule_weekly.md) — the backup policy will create restore points once a day on specific days.
* [Monthly](azure_fs_schedule_monthly.md) — the backup policy will create restore points once a month on a specific day.

Combining multiple schedule types together allows you to keep restore points for longer periods of time. For more information, see [Enabling Harmonized Scheduling](azure_fs_harmonized_scheduling.md).

Page updated 2026-07-01

