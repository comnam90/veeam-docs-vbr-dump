---
title: "Step 6. Specify Policy Scheduling Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_schedule_retention_fsx.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Specify Policy Scheduling Options


You can instruct the backup appliance to start the backup policy automatically according to a specific backup schedule. The backup schedule defines how often data stored in file systems added to the backup policy must be backed up.

|  |
| --- |
| Note |
| If some of the file systems that you plan to protect have daily automatic backup enabled or a weekly maintenance window configured, you must take into account that automatic backup and maintenance window have a higher priority. If you schedule a backup policy to run approximately at the same time when automatic backup or maintenance window starts, the backup policy will be queued. |

To help you implement a comprehensive backup strategy, the backup appliance allows you to create schedules of the following types:

* [Daily](aws_schedule_daily_fsx.md) — the backup policy will create restore points repeatedly throughout a day on specific days.
* [Weekly](aws_schedule_weekly_fsx.md) — the backup policy will create restore points once a day on specific days.
* [Monthly](aws_schedule_monthly_fsx.md) — the backup policy will create restore points once a month on a specific day.
* [Yearly](aws_schedule_yearly_fsx.md) — the backup policy will create restore points once a year on a specific day.

Combining multiple schedule types together allows you to retain restore points for longer periods of time. For more information, see [Enabling Harmonized Scheduling](aws_harmonized_scheduling_efs.md).

|  |
| --- |
| Note |
| If you do not specify the backup schedule, after you configure the backup policy, you will need to start it manually to create FSx file system backups. For information on how to start backup policies, see [Starting and Stopping Policies](aws_policies_start_stop.md). |

Page updated 2026-05-21

