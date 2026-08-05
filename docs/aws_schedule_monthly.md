---
title: "Specifying Monthly Schedule"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_schedule_monthly.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Specifying Monthly Schedule


To create a monthly schedule for the backup policy, at the Schedule step of the wizard, do the following:

1. Set the Monthly schedule toggle to On and click Edit Monthly Settings.
2. [Applies only if you enabled backup archiving at the [step 6](aws_add_policy_target_settings_backups.md#enable_archiving) step of the wizard] In the Choose monthly backup target section of the opened window, choose whether you want to store monthly backups in the archive backup repository.

If you set the Send backups to archive toggle to On, follow the instructions provided in section [Enabling Backup Archiving](aws_backup_archiving.md).

1. In the Create monthly schedule section, select months when the backup policy will create cloud-native snapshots, snapshot replicas or image-level backups.

|  |
| --- |
| Note |
| The backup appliance do not create snapshot replicas and image-level backups independently from cloud-native snapshots. That is why when you select months to create snapshot replicas and image-level backups, the same months are automatically selected for cloud-native snapshots. To learn how backup appliances perform backup, see [EC2 Backup](aws_backup_hiw_ec2.md). |

1. Use the Create restore points at and Run on drop-down lists to schedule a specific time and day for the backup policy to run.

|  |
| --- |
| Notes |
| * If you have selected a specific time for the backup policy to run at the Weekly schedule section of the Schedule step of the wizard, you will not be able to change the time for the monthly schedule unless you select the On day option.  * If you select the On day option, [harmonized scheduling](aws_harmonized_scheduling.md) cannot be guaranteed. Plus, to support the On day option, the backup appliance will require to create an additional temporary restore point if there are no other schedules planned to run on that day. However, the temporary restore point will be removed from AWS during the Backup Retention process from AWS in approximately 24 hours, to reduce unexpected infrastructure charges. |

1. In the Monthly retention section, configure retention policy settings for the monthly schedule:

* For cloud-native snapshots and snapshot replicas, specify the number of restore points that you want to keep in cloud-native snapshot and snapshot replica chains.

If the restore point limit is exceeded, the backup appliance removes the earliest restore point from each chain. For more information, see [EC2 Snapshot Retention](aws_retention_snapshots.md).

* For image-level backups, specify the number of days (or months) for which you want to keep restore points in a backup chain.

If a restore point is older than the specified time limit, the backup appliance removes the restore point from the chain. For more information, see [EC2 Backup Retention](aws_retention_backup.md).

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| The backup appliance will start applying the configured retention settings as soon as the backup policy produces restore points. Even if you disable the monthly schedule after the restore points are created, the retention policy will still be applied to these restore points. As a workaround, you can modify the configured retention settings. |

Considerations and Limitations

When you configure retention policy settings, consider the following:

* For the backup appliance to be able to use the [Changed Block Tracking](aws_cbt.md) (CBT) mechanism when processing EC2 instance data, you must keep at least one cloud-native snapshot in the snapshot chain.

* Regardless of the number of restore points that you specify, the backup appliance permanently retains an additional cloud-native snapshot in the chain by design, which is required for proper CBT functioning.

* It is recommended that you do not set the Snapshots to keep value to 0. Otherwise, the backup appliance will not be able to use the CBT mechanism, and it may take significantly more time to create incremental backups.

To learn how the CBT mechanism works, see [Changed Block Tracking](aws_cbt.md).

[![Creating EC2 Backup Policy](images/aws_schedule_monthly.webp)](images/aws_schedule_monthly.webp "Creating EC2 Backup Policy")

Page updated 2026-05-22

