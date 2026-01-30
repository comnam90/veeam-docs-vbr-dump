---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/dbconfig_before_you_begin.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you configure database connection settings, consider the following:

* If you change the database to which Veeam Backup & Replication must be connected, make sure that the database to which Veeam Backup & Replication is currently connected is available. If not, you must stop the Veeam Backup Service on the machine where Veeam Backup & Replication is installed.

* Do not connect Veeam Backup & Replication to the database which is being used by another Veeam Backup & Replication. In that case, Veeam Backup & Replication will not be able to utilize the encrypted data stored in this database. If you want to migrate the configuration database, see [Migrating Configuration Database to Another SQL Server](vbr_config_migrate_to_another_server.md) or [Migrating Configuration Database to PostgreSQL Server](vbr_config_migrate_to_postgresql.md).

* When you migrate the configuration database to another server, you must use the Microsoft SQL Server credentials that have CREATE ANY DATABASE permission on the target Microsoft SQL Server. For details, see [Microsoft Docs](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver15).

After database creation this account automatically gets a db\_owner role and can perform all operations with the database. If the current account does not have this permission, a Database Administrator may create an empty database in advance and grant the db\_owner role to the account that will be used for migration of the configuration database.


