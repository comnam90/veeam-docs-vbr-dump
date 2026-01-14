---
title: "Performing Full Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_protection_full.html"
last_updated: "10/23/2024"
product_version: "13.0.1.1071"
---

# Performing Full Backup

In this article

IBM Db2 supports the following types of full backups:

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

where <database\_name> is a name of the database you want to deactivate.

1. Back up the database offline with the following command:

|  |
| --- |
| db2 backup database <database\_name> load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so |

where <database\_name> is a name of the database you want to back up.

1. Re-activate the database.

|  |
| --- |
| db2 activate database <database\_name> |

where <database\_name> is a name of the database you want to deactivate.

Online Backup

To back up database online, do the following steps:

1. Before you back up database online, check if you set Veeam Plug-In to use the logarchmeth1 parameter.

If you have not configured the logarchmeth1 parameter during the [Veeam Plug-In configuration](db2_configure.md), you can configure the parameter using DB2ConfigTool:

|  |
| --- |
| DB2ConfigTool --set-logarchmeth yes |

Alternatively, you can re-configure the database with the following command:

|  |
| --- |
| db2 update database cfg for <database\_name> using logarchmeth1 VENDOR:</opt/veeam/VeeamPluginforDB2/libDB2Plugin.so> |

where <database\_name> is a name of the database you want to back up.

1. Back up the database online with the following command:

|  |
| --- |
| db2 backup database <database\_name> online load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so |

where <database\_name> is a name of the database you want to back up.

If you want to include logs in the backup, you can use the INCLUDE LOGS option with the BACKUP DATABASE command:

|  |
| --- |
| db2 backup database <database\_name> online load /opt/veeam/VeeamPluginforDB2/libDB2Plugin.so include logs |

where <database\_name> is a name of the database you want to back up.

To learn more about the INCLUDE LOGS option, see [this IBM article](https://www.ibm.com/docs/en/db2/11.5?topic=management-including-log-files-backup-image).

Page updated 10/23/2024

Page content applies to build 13.0.1.1071
