---
title: "Restoring Exported Database"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_export_restore_exported_databases.html"
last_updated: "1/17/2024"
product_version: "13.0.1.1071"
---

# Restoring Exported Database


Veeam Explorer for PostgreSQL exports databases to the target destination as DUMP files. These files are portable across platforms and can be used to restore the original state of the databases with the pg\_restore utility. For more information about this utility, see the [PostgreSQL Documentation](https://www.postgresql.org/docs/16/app-pgrestore.html).

To restore an exported database, save the DUMP file to the necessary PostgreSQL server and run the following command:

|  |
| --- |
| $ pg\_restore -p <port> -U <user> [-C] -d <database> <dump\_file> |

where:

* <port> is the instance port.
* <user> is the user or owner of the database.
* -C creates a new database. Use this argument only if you want the pg\_restore utility to create a new database.

Note that if you create a new database and the database in the DUMP file has tablespaces, you must manually create tablespaces with the same names as the ones in the DUMP file. The --no-tablespace argument of the pg\_restore utility, which places databases in the default tablespace, is not supported for DUMP files exported with Veeam Explorer for PostgreSQL.

* <database> may stand for different databases depending on whether or not you use the -C argument.

* If you use the -C argument, <database> is the name of the database that pg\_restore uses to run the necessary commands for restoring the database in the DUMP file, such as CREATE DATABASE.
* If you do not use the -C argument, <database> is the name of the target database. You can use the -c argument to overwrite the target database with the one in the DUMP file.

* <dump\_file> is the path to the DUMP file.

For example:

|  |
| --- |
| $ pg\_restore -p 5433 -U root -C -d sales /var/tmp/Import/export.dump |


