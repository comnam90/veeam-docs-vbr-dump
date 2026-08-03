---
title: "Creating SQL Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sql_backup_create.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Creating SQL Backup Policies


|  |
| --- |
| Important |
| SQL backup policies can protect only Azure SQL databases running on SQL Servers and databases located on SQL Managed Instances. If you want to protect a database hosted by a SQL Server on Azure VM, create an [Azure VM backup policy](azure_performing_vm_backup.md). Note that in this case, you will not be able to restore a single database without restoring the entire VM. |

To create a backup policy, do the following:

1. [Launch the Add Azure SQL Policy wizard](azure_sql_backup_wizard.md).
2. [Specify a backup policy name and description](azure_sql_backup_name.md).
3. [Configure backup source settings](azure_sql_backup_source_settings.md).
4. [Configure processing options](azure_sql_processing_options.md).
5. [Create a schedule for the backup policy](azure_sql_backup_policy_schedule.md).
6. [Specify automatic retry, health check and notification settings for the backup policy](azure_sql_backup_retry_notifications.md).
7. [Review the estimated cost of protecting the selected Azure SQL databases](azure_sql_backup_cost.md).
8. [Finish working with the wizard](azure_sql_backup_finish.md).

Page updated 2025-02-18

