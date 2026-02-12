---
title: "Performing Incremental Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_protection_incremental.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Performing Incremental Backup


After you created a full backup of the database, you can create the following types of incremental backups:

* An incremental backup. The incremental backup contains all database data that has changed since the last successful full backup.
* An incremental delta (or delta) backup. The delta backup contains all database data that has changed since the last successful full, incremental, or delta backup.

|  |
| --- |
| Important |
| To create incremental and delta backups, you must set the trackmod parameter before you create a full backup. For details, see [Preparing Database](db2_protection_prepare.md#increment). |

You can create both incremental and delta backups offline and online. For details, see the following subsections:

* [Offline backup](#offline)
* [Online backup](#online)

Offline Backup

To back up database offline, do the following steps:

1. Offline backup requires downtime. During the downtime, the database is offline and inaccessible to applications. To prepare the database, do the following steps:

1. Find all the applications with existing connections to IBM Db2.

|  |
| --- |
| db2 list applications |

This command returns a list of all existing connections. To stop these connections, you can close the applications manually or you can disconnect all connections to all IBM Db2 databases with the following command:

|  |
| --- |
| db2 force application all |

1. Deactivate the database you want to back up offline with the following commands:

|  |
| --- |
| db2 deactivate database <database\_name> |

where <database\_name> is the name of the database you want to deactivate.

1. Depending on the type of the backup you want to create, back up the database offline with one of the following commands:

* To create an incremental backup, use the following command:

|  |
| --- |
| db2 backup database <database\_name> incremental load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so |

where <database\_name> is the name of the database you want to back up.

* To create a delta backup, use the following command:

|  |
| --- |
| db2 backup database <database\_name> incremental delta load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so |

where <database\_name> is the name of the database you want to back up.

1. Re-activate the database.

|  |
| --- |
| db2 activate database <database\_name> |

where <database\_name> is the name of the database you want to deactivate.

Online Backup

Depending on the type of the backup you want to create, back up the database online with one of the following commands:

* To create an incremental backup, use the following command:

|  |
| --- |
| db2 backup database <database\_name> online incremental load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so |

where <database\_name> is the name of the database you want to back up.

* To create a delta backup, use the following command:

|  |
| --- |
| db2 backup database <database\_name> online incremental delta load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so |

where <database\_name> is the name of the database you want to back up.

If you want to include logs in the backup, you can use the INCLUDE LOGS option with the BACKUP DATABASE command:

|  |
| --- |
| db2 backup database <database\_name> online load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so include logs |

where <database\_name> is the name of the database you want to back up.

To learn more about the INCLUDE LOGS option, see [this IBM article](https://www.ibm.com/docs/en/db2/11.5?topic=management-including-log-files-backup-image).


