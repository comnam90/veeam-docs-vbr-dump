---
title: "Step 7. Specify Policy Scheduling Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_schedule_retention_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 7. Specify Policy Scheduling Options


You can instruct the backup appliance to start the backup policy automatically according to a specific backup schedule. The backup schedule defines how often data of the instances added to the backup policy must be backed up.

|  |
| --- |
| Important |
| * If you have selected a standard or an archive backup repository with immutability settings enabled at [step 4](aws_add_policy_target_settings_backups_rds.md) of the wizard, you must configure at least one schedule for the backup policy. * [Applies only to Microsoft SQL Server DB instances] If any of the DB instances that you plan to protect have a backup or a maintenance window configured, make sure that these windows do not overlap with the backup policy schedule. Otherwise, the backup operation may fail to complete successfully.   For more information on the backup and maintenance windows, see AWS Documentation, sections [Maintaining DB Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_UpgradeDBInstance.Maintenance.html?utm_source=chatgpt.com) and [Managing Automated Backups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ManagingAutomatedBackups.html).   * [Applies only to Microsoft SQL Server DB instances] It is not recommended that you manually take Amazon DB snapshots using the AWS Management Console during backup sessions. Otherwise, the backup operation will fail to complete successfully.   For more information on Amazon DB snapshots, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateSnapshot.html). |

To help you implement a comprehensive backup strategy, the backup appliance allows you to create schedules of the following types:

* [Daily](aws_schedule_daily_rds.md) — the backup policy will create restore points repeatedly throughout a day on specific days.
* [Weekly](aws_schedule_weekly_rds.md) — the backup policy will create restore points once a day on specific days.
* [Monthly](aws_schedule_monthly_rds.md) — the backup policy will create restore points once a month on a specific day.
* [Yearly](aws_schedule_yearly_rds.md) — the backup policy will create restore points once a year on a specific day.

Combining multiple schedule types together allows you to retain restore points for longer periods of time. For more information, see [Enabling Harmonized Scheduling](aws_harmonized_scheduling_rds.md).

|  |
| --- |
| Note |
| If you do not specify the backup schedule after you configure the backup policy, you will need to start it manually to create RDS snapshots and backups. For information on how to start backup policies, see [Starting and Stopping Policies](aws_policies_start_stop.md). |

Page updated 2026-05-21

