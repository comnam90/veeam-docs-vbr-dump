---
title: "Removing SMTP and Database Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_accounts_smtp_database_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing SMTP and Database Accounts


The backup appliance allows you to permanently remove an SMTP or database account from the configuration database if you no longer need it:

1. Switch to the Configuration page.
2. Navigate to Accounts > Accounts.
3. Select the account and click Remove.

|  |
| --- |
| Important |
| You cannot remove a database account that is associated with any backup policy. [Modify the settings of all the related policies](azure_backup.md) to remove references to the account — and then try removing the account again. |

[![Removing Accounts](images/azure_smtp_db_account_delete.webp)](images/azure_smtp_db_account_delete.webp "Removing Accounts")

Page updated 2026-07-01

