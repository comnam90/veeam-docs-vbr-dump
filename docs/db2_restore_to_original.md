---
title: "Restore to Original Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_original.html"
last_updated: "11/25/2025"
product_version: "13.0.1.1071"
---

# Restore to Original Server

In this article

You can restore IBM Db2 databases from backups stored on Veeam backup repositories in the following ways:

* [Restore from a full backup](#full).
* [Restore from an incremental backup](#incremental).
* [Restoring to the previous state](#logs).

Restore from Full Backup

To restore a IBM Db2 database from a full backup, use the following command:

|  |
| --- |
| db2 restore db <database\_name> load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> |

where:

* <database\_name> is a name of the database you want to restore.
* <timestamp> is a time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In will restore database from the backup file created at the time that you specify in the command.

To learn how to get time stamp, see [Get Backup Time Stamp](db2_restore_get_time_stamp.md).

Restore from Incremental Backup

To restore a IBM Db2 database from an incremental backup, use the following command:

|  |
| --- |
| db2 restore db <database\_name> incremental automatic load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> |

where:

* <database\_name> is a name of the database you want to restore.
* <timestamp> is a time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In will restore database from the backup file created at the time that you specify in the command.

To learn how to get time stamp, see [Get Backup Time Stamp](db2_restore_get_time_stamp.md).

Restore to Previous State

You can restore the database to the previous states. In this case, you restore database from a backup, then apply archive logs that are available in the backup file. With these archive logs, you can restore database to the exact state when the backup was created.

|  |
| --- |
| Important |
| To restore database to the previous state, you must use a full online backup of the database. To learn more, see [Performing Full Backup](db2_protection_full.md). |

To restore database to the previous state, do the following steps:

1. Restore to the previous state requires downtime. Terminate all existing connections and deactivate the database with the following commands:

|  |
| --- |
| db2 terminate  db2 deactivate database <database\_name> |

where <database\_name> is a name of the database you want to deactivate.

1. Extract archive logs from the backup file with the following command:

|  |
| --- |
| db2 restore database <database\_name> logs load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so LOGTARGET <path\_to\_logs> |

where:

* <database\_name> is a name of the database you want to deactivate.
* <path\_to\_logs> is a path to the directory to which Veeam Plug-In will extract archive logs.

1. Return the database to the state recorded in a backup with the following command:

|  |
| --- |
| db2 restore database <database\_name> load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> replace existing |

where:

* <database\_name> is a name of the database you want to restore.
* <timestamp> is a time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In will restore database from the backup file created at the time that you specify in the command.

To learn how to get time stamp, see [Get Backup Time Stamp](db2_restore_get_time_stamp.md).

1. Apply archive logs to return database to the exact state when the backup was created with the following command:

|  |
| --- |
| db2 rollforward database <database\_name> to end of logs overflow log path (<path\_to\_logs>) |

where:

* <database\_name> is a name of the database you want to deactivate.
* <path\_to\_logs> is a path to the directory to which Veeam Plug-In will extract archive logs.

1. Recover the database with the following command:

|  |
| --- |
| db2 recover database <database\_name> |

where <database\_name> is a name of the database you want to deactivate.

1. Re-activate the database with the following command:

|  |
| --- |
| db2 activate database <database\_name> |

where <database\_name> is a name of the database you want to deactivate.

Page updated 11/25/2025

Page content applies to build 13.0.1.1071
