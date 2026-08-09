---
title: "Managing Database Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_accounts_database.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Database Accounts


To allow the backup appliance to authenticate against PostgreSQL DB instances protected by backup policies, you must specify credentials of database accounts that will be used to access the databases when performing [image-level backup](aws_add_policy_processing_settings_rds.md) and [restore operations](aws_restore_rds_database_settings.md).

|  |
| --- |
| Note |
| After you upgrade the backup appliance to version 11, the list of database accounts will be populated with policy credentials that were previously used to access protected databases. |

In This Section

* [Adding Database Accounts](aws_accounts_database_create.md)
* [Editing Database Accounts](aws_accounts_database_edit.md)
* [Removing Database Accounts](aws_accounts_database_remove.md)

Page updated 2026-05-20

