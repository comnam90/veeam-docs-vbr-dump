---
title: "Specifying Weekly Schedule"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_schedule_weekly_reshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Specifying Weekly Schedule


To create a weekly schedule for the backup policy, at the Schedule step of the wizard, do the following:

1. Set the Weekly schedule toggle to On and click Edit Weekly Settings.
2. In the Create weekly schedule section, select weekdays when the backup policy will create cluster backups.
3. Use the Create restore point at drop-down list to schedule a specific time for the backup policy to run.
4. In the Weekly retention section, specify the number of days (or months) for which you want to keep restore points in a backup chain.

If a restore point is older than the specified time limit, the backup appliance removes the restore point from the chain. For more information, see [Redshift Backup Retention](aws_retention_backup_redshift.md).

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| The backup appliance will start applying the configured retention settings as soon as the backup policy produces restore points. Even if you disable the weekly schedule after the restore points are created, the retention policy will still be applied to these restore points. As a workaround, you can modify the configured retention settings. |

[![Creating Redshift Backup Policy](images/aws_schedule_weekly_redshift.webp)](images/aws_schedule_weekly_redshift.webp "Creating Redshift Backup Policy")

Page updated 2026-05-21

