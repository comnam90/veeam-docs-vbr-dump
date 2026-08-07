---
title: "Removing Database Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_accounts_database_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Database Accounts


The backup appliance allows you to permanently remove a database account from the appliance configuration database if you no longer need it:

1. Switch to the Configuration page.
2. Navigate to Accounts > Database Accounts.
3. Select the account and click Remove.

|  |
| --- |
| Important |
| You cannot remove a database account that is associated with any backup policy. Delete all of the affected policies or [edit their settings](aws_policies_edit.md) — and then try removing the account again. |

[![Remove Database Account](images/aws_database_account_remove.webp)](images/aws_database_account_remove.webp "Remove Database Account")

Page updated 2026-05-21

