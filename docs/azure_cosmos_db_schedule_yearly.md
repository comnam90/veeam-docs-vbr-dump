---
title: "Specifying Yearly Schedule"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_cosmos_db_schedule_yearly.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Specifying Yearly Schedule


To create a yearly schedule for the backup policy, do the following at the Schedule step of the wizard:

1. Set the Yearly retention toggle to On and click Edit Yearly Settings.
2. In the Yearly schedule window, specify a day, month and time when the backup policy will create backups.

|  |
| --- |
| Notes |
| * If you have selected a specific time for the backup policy to run at the Weekly schedule or Monthly schedule sections of the Schedule step of the wizard, you will not be able to change the time for the yearly schedule unless you select the On Day option from the Create restore point on drop-down list. * If you select the On Day option, [harmonized scheduling](azure_vm_harmonized_scheduling.md) cannot be guaranteed. Plus, to support the On Day option, the backup appliance will require to create an additional temporary restore point if there are no other schedules planned to run on that day. However, the temporary restore point will be removed from Microsoft Azure during the Backup Retention process in approximately 24 hours, to reduce unexpected infrastructure charges. |

1. In the Keep backups for field, specify the number of years for which you want to keep restore points in a backup chain.

If a restore point is older than the specified time limit, the backup appliance removes the restore point from the chain. For more information, see [Cosmos DB Backup Retention](azure_cosmos_db_backup_retention.md).

1. In the Repository section, select a repository where the created backups will be stored.

For a repository to be displayed in the Repository list, it must be added to Veeam Backup for Microsoft Azure as described in section [Adding Backup Repositories](azure_repository_add_ui.md) or [Adding Storage Vaults](azure_repository_vdc_add_ui.md).

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| The backup appliance will start applying the configured retention settings as soon as the backup policy produces restore points. Even if you disable the daily schedule after the restore points are created, the retention policy will still be applied to these restore points. As a workaround, you can modify the configured retention settings. |

[![Adding Backup Policy](images/azure_cosmos_db_schedule_yearly.webp)](images/azure_cosmos_db_schedule_yearly.webp "Adding Backup Policy")

Page updated 2026-07-01

