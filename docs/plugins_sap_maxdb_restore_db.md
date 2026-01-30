---
title: "Restore to Original Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_restore_db.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---

# Restore to Original Server


To restore SAP MaxDB database to the original server, you can perform the following operations using Database Manager CLI:

* [Collect database information](#collect)
* [Perform restore](#restore)

Collect Database Information

To collect information that is required for the database restore, do the following:

1. Enter Database Manager CLI:

|  |
| --- |
| /opt/sdb/programs/bin/dbmcli -uUTL -d <database> -u <login>,<password> |

where:

* <database> is a database name
* <user> is a name for the database user has administrator rights
* <password> is a password for the database user has administrator rights

For example:

|  |
| --- |
| /opt/sdb/programs/bin/dbmcli -uUTL -d MAXDB1 -u DBADMIN,SECRET |

1. Fetch the current backup history into the main memory:

|  |
| --- |
| backup\_history\_open |

1. Display the content of the backup history that you fetched in the previous step:

|  |
| --- |
| backup\_history\_list |

This command displays the list of all previously performed database backup and restore actions. This information allows you to review existing backups that you can use to restore data and collect required information.

For example:

|  |
| --- |
| 68E79D4F0006|             |HISTLOST |2025-10-09 13:32:31|                   |2025-10-09 13:32:31|                   |          |          |   |                                                                |          |          |         0|                                        | |

1. Fetch information stored in the Veeam Backint for a certain database backup type:

|  |
| --- |
| backup\_ext\_ids\_get <medium\_name> <database> |

where:

* <medium\_name> is the medium that you assigned during the [database configuration](plugins_sap_maxdb_deploy_configure_db.md). To understand which media are available for restore, review the [backup history file](#history).

For example, you can select the following media from the [database configuration](plugins_sap_maxdb_deploy_configure_db.md):

* VEEAMDATA is a media for a full data backup
* VEEAMPAGES is a media for an incremental data backup
* VEEAMLOG is a media for an interactive log backup

* <database> is the name of the database using which the backups were created

For example:

|  |
| --- |
| backup\_ext\_ids\_get VEEAMDATA MAXDB1 |

1. Display the information from the Veeam Backint that you fetched in the previous step:

|  |
| --- |
| backup\_ext\_ids\_list |

This command displays information about a certain database and backup type. This information includes the following details for each backup: external backup ID, availability status, backup type and the time the backup was created.

For example:

|  |
| --- |
| AVAILABLE|MAXDB1 A1F7FEDCA7700BE0 /tmp/MAXDB1/compipe1|DATA  MIGRATION|2025-10-09 19:09:45| AVAILABLE|MAXDB1 6BDD1FAA716643CE /tmp/MAXDB1/compipe2|DATA  MIGRATION|2025-10-09 19:09:45| AVAILABLE|MAXDB1 7426C47F91789FCF /tmp/MAXDB1/compipe3|DATA  MIGRATION|2025-10-09 19:09:45| AVAILABLE|MAXDB1 F30423029579B4CF /tmp/MAXDB1/compipe4|DATA  MIGRATION|2025-10-09 19:09:45| |

After you collected database information, you can perform database restore.

Perform restore

To restore database, do the following:

1. Enter Database Manager CLI:

|  |
| --- |
| /opt/sdb/programs/bin/dbmcli -uUTL -d <database> -u <login>,<password> |

where:

* <database> is a database name
* <user> is a name for the database user has administrator rights
* <password> is a password for the database user has administrator rights

For example:

|  |
| --- |
| /opt/sdb/programs/bin/dbmcli -uUTL -d MAXDB1 -u DBADMIN,SECRET |

1. Switch database to the ADMIN operational state:

|  |
| --- |
| db\_admin |

1. Restore the database with the recover\_start command:

|  |
| --- |
| recover\_start <medium\_name> <backup\_type> <label> EBID <ebid\_list> |

where:

* <medium\_name> is medium that you assigned during the database configuration. To understand which media are available for restore, review the [backup history file](#history) and the output of the medium\_getall command.

For example, you can select the following media:

* VEEAMDATA is a media for a full data backup
* VEEAMPAGES is a media for an incremental data backup
* VEEAMLOG is a media for an interactive log backup

* <backup\_type> is the type of backup that you want to restore. To understand which backup types are available for restore, check the output of the backup\_ext\_ids\_list command.

You can select the following backup types:

* DATA is a full data backup
* PAGES is an incremental data backup
* LOG is an interactive log backup

* <label> is an ID of a backup that you want to use. To get backup IDs, review the [backup history file](#history).
* <ebid\_list>  is a list of external backup IDs that you want to restore. If the list contains several external backup IDs, separate them by commas. If the backup IDs contain spaces, the list must be enclosed in double quotation marks. To get external backup IDs, review the [information from the Veeam Backint](#backint).

To learn more about the recover\_start command, see [SAP MaxDB documentation](https://maxdb.sap.com/doc/7_7/45/ad0ae6ebaf47f6e10000000a114a6b/frameset.htm).

For example:

|  |
| --- |
| recover\_start VEEAMDATA DATA DAT\_000000001 EBID "MAXDB1 A1F7FEDCA7700BE0 /tmp/MAXDB1/compipe1,MAXDB1 6BDD1FAA716643CE /tmp/MAXDB1/compipe2,MAXDB1 7426C47F91789FCF /tmp/MAXDB1/compipe3,MAXDB1 F30423029579B4CF /tmp/MAXDB1/compipe4" |


