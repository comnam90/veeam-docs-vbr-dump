---
title: "Removing SQL Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_removing_sql_backups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing SQL Backups


The backup appliance applies the [configured retention policy settings](azure_sql_backup_policy_schedule.md) to automatically remove backups created for SQL databases by backup policies. If necessary, you can also remove the backed-up data manually.

|  |
| --- |
| Important |
| Do not delete backups from Microsoft Azure storage accounts in the Microsoft Azure portal. If some backup in a backup chain is missing, you will not be able to roll back Azure SQL database data to the necessary state. |

To remove backed-up data manually, do the following:

1. Navigate to Protected Data > Databases > Azure SQL.

1. Select Azure SQL databases whose data you want to remove.

1. Click Remove and select either of the following options:

* All — to remove all backups created for the selected Azure SQL databases both by backup policies and manually.
* Backups — to remove all backups created in repositories for the selected Azure SQL databases.
* Archive — to remove all backups created in archive repositories for the selected Azure SQL databases.
* Manual — to remove all backups created for the selected Azure SQL databases manually.

[![Removing Backups](images/azure_remove_backups_sql.webp)](images/azure_remove_backups_sql.webp "Removing Backups")

Page updated 2026-07-01

