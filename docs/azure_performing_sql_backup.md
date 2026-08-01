---
title: "Performing SQL Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_performing_sql_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing SQL Backup


One backup policy can be used to process one or more Azure SQL databases within one Microsoft Entra tenant. The scope of data that you can protect in a tenant is limited by permissions of a service account that is specified in the backup policy settings.

Before you create an Azure SQL backup policy, check the following prerequisites:

* If you plan to create backups of Azure SQL databases, backup infrastructure components that will take part in the backup process must be added to the backup infrastructure and configured properly. These include [repositories](azure_repositories.md) and [worker instances](azure_workers.md).
* If you plan to receive email notifications on backup policy results, configure email notification settings first. For more information, see [Configuring Global Notification Settings](azure_configuring_notification_settings.md).

To schedule data protection tasks to run automatically, [create backup policies](azure_sql_backup_create.md). For each protected Azure SQL database, you can also [take a backup manually](azure_creating_sql_backups_manually.md) when needed.

|  |
| --- |
| Important |
| Veeam Plug-in for Microsoft Azure does not allow you to protect databases hosted by Azure Arc-enabled SQL Managed Instances and SQL Servers on Azure Arc-enabled servers. |

Page updated 2026-07-01

