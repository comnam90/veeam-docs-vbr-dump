---
title: "Performing Scheduled Configuration Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuring_backup_schedule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Scheduled Configuration Backup


While performing configuration backup, the backup appliance exports data from the configuration database and saves it to a backup file in a backup repository. To instruct the backup appliance to back up the configuration database of the backup appliance automatically by schedule, do the following:

1. Switch to the Configuration page.
2. Navigate to Configuration Backup.
3. In the Backup schedule section, set the Enable scheduling toggle to On.
4. Click Choose in the Repository field, and use the list of available repositories in the Choose Repository window to select a backup repository where configuration backups will be stored.

For a backup repository to be displayed in the list of available repositories, it must be added to the backup appliance as described in section [Adding Backup Repositories](azure_repository_add_ui.md). The list shows only backup repositories that have encryption enabled and immutability disabled.

1. In the Keep restore points for field, specify the number of days for which you want to keep restore points in a backup chain in the selected backup repository.

If a restore point is older than the specified time limit, the backup appliance removes the restore point from the chain. For more information, see [VM Backup Retention](azure_vm_backup_retention.md), [SQL Backup Retention](azure_sql_backup_retention.md) and [Cosmos DB Backup Retention](azure_cosmos_db_backup_retention.md) .

1. In the Create daily backup at field, choose whether configuration backups will be created every day, on weekdays (Monday through Friday), or on specific days.
2. Click Save.

[![Creating Configuration Backup Manually](images/azure_config_backup_schedule.webp)](images/azure_config_backup_schedule.webp "Creating Configuration Backup Manually")

Page updated 2026-07-01

