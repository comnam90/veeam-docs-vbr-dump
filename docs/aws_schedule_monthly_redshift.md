---
title: "Specifying Monthly Schedule"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_schedule_monthly_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Specifying Monthly Schedule


To create a monthly schedule for the backup policy, at the Schedule step of the wizard, do the following:

1. Set the Monthly schedule toggle to On and click Edit Monthly Settings.
2. In the Create monthly schedule section, select months when the backup policy will create cluster backups.
3. Use the Create restore point at and Run on drop-down lists to schedule a specific time and day for the backup policy to run.

|  |
| --- |
| Notes |
| * If you have selected a specific time for the backup policy to run at the Weekly schedule section of the Schedule step of the wizard, you will not be able to change the time for the monthly schedule unless you select the On day option.  * If you select the On day option, [harmonized scheduling](aws_harmonized_scheduling_redshift.md) cannot be guaranteed. |

1. In the Monthly retention section, specify the number of days (or months) for which you want to keep restore points in a backup chain.

If a restore point is older than the specified time limit, the backup appliance removes the restore point from the chain. For more information, see [Redshift Backup Retention](aws_retention_backup_redshift.md).

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| The backup appliance will start applying the configured retention settings as soon as the backup policy produces restore points. Even if you disable the monthly schedule after the restore points are created, the retention policy will still be applied to these restore points. As a workaround, you can modify the configured retention settings. |

[![Creating Redshift Backup Policy](images/aws_schedule_monthly_redshift.webp)](images/aws_schedule_monthly_redshift.webp "Creating Redshift Backup Policy")

Page updated 2026-05-21

