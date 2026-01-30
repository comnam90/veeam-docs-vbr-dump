---
title: "Restore to Instance with Different Name"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_server_with_different_name.html"
last_updated: "11/25/2025"
product_version: "13.0.1.1071"
---

# Restore to Instance with Different Name


If you plan to restore to a instance with a name that is different from the backed-up instance, see you must perform a redirected restore. To learn more, see [this IBM article](https://www.ibm.com/docs/en/db2/11.5?topic=restore-performing-redirected-operation).

For example, you can use the SET STOGROUP PATHS command. With this command, you can set storage group paths for the database you want to restore. If you selected this approach, do the following steps:

1. Run the RESTORE command with the REDIRECT parameter:

|  |
| --- |
| db2 restore database <database\_name> load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> REDIRECT |

where:

* <database\_name> is a name of the database you want to restore.
* <timestamp> is a time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In will restore database from the backup file created at the time that you specify in the command.

1. Set storage group paths for the database with the following command:

|  |
| --- |
| db2 set stogroup paths for IBMSTOGROUP on '/home/<instance\_name>' |

where: <instance\_name> is a name of the target instance to which you want to restore your database.

1. Run the RESTORE command again with the CONTINUE parameter:

|  |
| --- |
| db2 restore database <database\_name> continue |

where <database\_name> is a name of the database you want to restore.

After that, your database will be restored and re-configured to comply with the name of the target instance.


