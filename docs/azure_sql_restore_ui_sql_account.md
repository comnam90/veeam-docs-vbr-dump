---
title: "Step 5. Select Azure SQL Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sql_restore_ui_sql_account.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Select Azure SQL Account


[This step applies only if you have selected the Restore to the original location option at the Restore Mode step of the wizard]

At the SQL account step of the wizard, select an Azure SQL Server account that will be used to authenticate against the SQL Server that will host the restored database.

1. Click Instance.
2. In the Choose a SQL server account to use window, select the necessary Azure SQL Server account and click Apply.

For an Azure SQL Server account to be displayed in the list of available accounts, it must be added to the backup appliance as described in section [Adding SMTP and Database Accounts](azure_accounts_smtp_database_create.md).

|  |
| --- |
| Important |
| Portal Operators and Restore Operators can use only those Azure SQL Server accounts that have been specified for the SQL Server in settings of any backup policy created by a Portal Administrator. |

[![Performing SQL Restore](images/azure_sql_restore_sql_account.webp)](images/azure_sql_restore_sql_account.webp "Performing SQL Restore")

Page updated 2026-07-17

