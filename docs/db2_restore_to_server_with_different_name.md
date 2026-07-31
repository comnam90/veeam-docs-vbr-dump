---
title: "Restore to Instance with Different Name"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_server_with_different_name.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restore to Instance with Different Name


If you plan to restore to an instance with a name that is different from the backed-up instance, you must perform a redirected restore. To learn more, see [this IBM article](https://www.ibm.com/docs/en/db2/11.5?topic=restore-performing-redirected-operation).

To do this, you can use the set stogroup paths command. With this command, you can set storage group paths for the database you want to restore. If you selected this approach, do the following steps:

1. Run the restore command with the redirect parameter using one of the following commands depending on the OS you are using:

* For Linux or Unix:

|  |
| --- |
| db2 restore database <database\_name> load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> redirect |

* For Microsoft Windows:

|  |
| --- |
| db2 restore database <database\_name> load 'C:\Program Files\Veeam\VeeamPluginforDB2\DB2Plugin.dll' taken at <timestamp> redirect |

where:

* <database\_name> is the name of the database you want to restore.
* <timestamp> is the time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In will restore database from the backup file created at the time that you specify in the command.

1. Set storage group paths for the database with the following command:

|  |
| --- |
| db2 set stogroup paths for IBMSTOGROUP on '<path>' |

where <path> is the path to the target instance to which you want to restore your database.

For example:

* For Linux or Unix:

|  |
| --- |
| db2 set stogroup paths for IBMSTOGROUP on '/db2/<instance\_name>' |

* For Microsoft Windows:

|  |
| --- |
| db2 set stogroup paths for IBMSTOGROUP on 'C:\DB2\<instance\_name>' |

1. Run the restore command again with the continue parameter:

|  |
| --- |
| db2 restore database <database\_name> continue |

where <database\_name> is the name of the database you want to restore.

After that, your database will be restored and re-configured to comply with the name of the target instance.

Page updated 2026-07-02

