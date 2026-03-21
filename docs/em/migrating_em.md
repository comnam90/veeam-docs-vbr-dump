---
title: "Migrating Enterprise Manager"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/migrating_em.html"
last_updated: "3/19/2026"
product_version: "13.0.1.2067"
---

# Migrating Enterprise Manager


You can migrate Veeam Backup Enterprise Manager, its configuration database or both to another server.

Before you migrate Enterprise Manager, you must export Enterprise Manager keysets and prepare the credentials stored in the Enterprise Manager configuration database so you will be able to re-enter the credentials on a new server. If you migrate the Enterprise Manager configuration database only, the credentials and keysets will remain valid.

|  |
| --- |
| Note |
| If you want to migrate the Enterprise Manager configuration database from one Microsoft SQL Server instance to another or from one PostgreSQL instance to another, contact [Veeam Customer Support](https://www.veeam.com/support.html). |

In This Section

* [Migrating Enterprise Manager from Microsoft SQL Server to PostrgeSQL](em_db_migration.md)
* [Connecting Enterprise Manager to Another Configuration Database](dbconfig_utility.md)


