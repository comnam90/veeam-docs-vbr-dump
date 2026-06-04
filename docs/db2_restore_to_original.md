---
title: "Restore to Original Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_original.html"
last_updated: "6/3/2026"
product_version: "13.0.2.29"
---

# Restore to Original Server


You can restore IBM Db2 databases from backups stored on Veeam backup repositories in the following ways:

* [Restore from a full backup](#full).
* [Restore from an incremental backup](#incremental).
* [Restoring to the previous state](#logs).
* [Restore to a specific point in time](#pit).

Restore from Full Backup

To restore a IBM Db2 database from a full backup, use the following command:

|  |
| --- |
| db2 restore db <database\_name> load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> |

where:

* <database\_name> is the name of the database you want to restore.
* <timestamp> is the time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In restores database from the backup file created at the time that you specify in the command.

To learn how to get time stamp, see [Get Backup Time Stamp](db2_restore_get_time_stamp.md).

Restore from Incremental Backup

To restore a IBM Db2 database from an incremental backup, use the following command:

|  |
| --- |
| db2 restore db <database\_name> incremental automatic load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> |

where:

* <database\_name> is the name of the database you want to restore.
* <timestamp> is the time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In restores database from the backup file created at the time that you specify in the command.

To learn how to get time stamp, see [Get Backup Time Stamp](db2_restore_get_time_stamp.md).

Restore to Previous State

You can restore the database to the previous state. To do that, you restore the database from a backup, then apply archive logs that are available in the backup file. With these archive logs, you can restore the database to the exact state when the backup was created.

|  |
| --- |
| Important |
| To restore the database to the previous state, you must use a full online backup of the database. To learn more, see [Performing Full Backup](db2_protection_full.md). |

To restore the database to the previous state, do the following steps:

1. Restore to the previous state requires downtime. Terminate all existing connections and deactivate the database with the following commands:

|  |
| --- |
| db2 terminate  db2 deactivate database <database\_name> |

where <database\_name> is the name of the database you want to deactivate.

1. Extract archive logs from the backup file with the following command:

|  |
| --- |
| db2 restore database <database\_name> logs load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so LOGTARGET <path\_to\_logs> |

where:

* <database\_name> is the name of the database you want to restore.
* <path\_to\_logs> is the path to the directory to which Veeam Plug-In extracts archive logs.

1. Restore the database to the state recorded in a full online backup with the following command:

|  |
| --- |
| db2 restore database <database\_name> load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> replace existing |

where:

* <database\_name> is the name of the database you want to restore.
* <timestamp> is the time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In restores the database from the backup file created at the time that you specify in the command.

To learn how to get time stamp, see [Get Backup Time Stamp](db2_restore_get_time_stamp.md).

1. Apply archive logs to return the database to the exact state when the backup was created with the following command:

|  |
| --- |
| db2 rollforward database <database\_name> to end of logs overflow log path (<path\_to\_logs>) |

where:

* <database\_name> is the name of the database you want to restore.
* <path\_to\_logs> is the path to the directory containing the extracted archive logs.

1. Recover the database with the following command:

|  |
| --- |
| db2 recover database <database\_name> |

where <database\_name> is the name of the database you want to restore.

1. Re-activate the database with the following command:

|  |
| --- |
| db2 activate database <database\_name> |

where <database\_name> is the name of the database you want to activate.

Restore to Specific Point in Time

You can restore an IBM Db2 database to a specific point in time between two backups. Veeam Plug-In applies archive logs up to the target time, returning the database to the exact time that you specify.

|  |
| --- |
| Important |
| To restore a database to a specific point in time, you must use a full online backup of the database. To learn more, see [Performing Full Backup](db2_protection_full.md). |

To restore a database to a specific point in time, do the following steps:

1. Restore to a specific point in time requires downtime. Terminate all existing connections and deactivate the database with the following commands:

|  |
| --- |
| db2 terminate  db2 deactivate database <database\_name> |

where <database\_name> is the name of the database you want to deactivate.

1. Extract archive logs from the backup file with the following command:

|  |
| --- |
| db2 restore database <database\_name> logs load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so LOGTARGET <path\_to\_logs> |

where:

* <database\_name> is the name of the database you want to restore.
* <path\_to\_logs> is the path to the directory to which Veeam Plug-In extracts archive logs.

1. Restore the database to the state recorded in a full online backup with the following command:

|  |
| --- |
| db2 restore database <database\_name> load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so taken at <timestamp> replace existing |

where:

* <database\_name> is the name of the database you want to restore.
* <timestamp> is the time stamp that IBM Db2 generates for each backup in the yyyymmddhhmmss format. Veeam Plug-In restores the database from the backup file created at the time that you specify in the command.

To learn how to get time stamp, see [Get Backup Time Stamp](db2_restore_get_time_stamp.md).

1. Apply archive logs up to the target time stamp with the following command:

|  |
| --- |
| db2 rollforward database <database\_name> to <utc\_time> overflow log path (<path\_to\_logs>) and complete |

where:

* <database\_name> is the name of the database you want to restore.
* <utc\_time> is the UTC time in the YYYY-MM-DD-HH.MM.SS format to which you want to restore the database. The value must be between the time at which the online backup operation completed and the latest extracted archive log.

For details on how to use local time instead of the UTC time, see [IBM documentation](https://www.ibm.com/docs/en/db2/11.5.x?topic=commands-rollforward-database#r0001978__title__9).

* <path\_to\_logs> is the path to the directory containing the extracted archive logs.

For details on the rollforward command syntax, see [IBM documentation](https://www.ibm.com/docs/en/db2/11.5.x?topic=commands-rollforward-database).

1. Re-activate the database with the following command:

|  |
| --- |
| db2 activate database <database\_name> |

where <database\_name> is the name of the database you want to activate.


