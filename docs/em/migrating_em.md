---
title: "Migrating Enterprise Manager"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/migrating_em.html"
last_updated: "2026"
product_version: "13.0.2.29"
---

# Migrating Enterprise Manager


You can migrate Veeam Backup Enterprise Manager, its configuration database or both to another machine.

* To migrate the configuration database, use the Veeam.EM.DB.Migration.exe utility. You can migrate the Enterprise Manager configuration database only from Microsoft SQL Server to PostgreSQL. If you want to migrate the configuration database from one Microsoft SQL Server instance to another Microsoft SQL Server instance or from one PostgreSQL instance to another PostgreSQL instance, contact [Veeam Customer Support](https://www.veeam.com/support.html). For more information, see [Migrating Enterprise Manager from Microsoft SQL Server to PostrgeSQL](em_db_migration.md).
* To migrate Enterprise Manager to another machine, uninstall Enterprise Manager from the current machine and install it on a new one. If you also want to migrate the database, manually back up the database and restore it on a new machine. Use [the dbconfig tool](dbconfig_utility.md) to connect Enterprise Manager to a different configuration database. Before you migrate Enterprise Manager, you must export Enterprise Manager keysets and prepare the credentials stored in the Enterprise Manager configuration database so you will be able to re-enter the credentials on a new server. If you migrate the Enterprise Manager configuration database only, the credentials and keysets will remain valid.

In This Section

* [Migrating Enterprise Manager from Microsoft SQL Server to PostrgeSQL](em_db_migration.md)
* [Connecting Enterprise Manager to Another Configuration Database](dbconfig_utility.md)

Page updated 2026-07-09

