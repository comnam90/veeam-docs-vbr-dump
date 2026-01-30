---
title: "SAP MaxDB Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_backup_backint.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---

# SAP MaxDB Backup


To back up SAP MaxDB databases, you can use Database Manager CLI:

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

1. Then, you will need to use the command backup\_start to start the backup, choosing the medium you want to use:

|  |
| --- |
| backup\_start <medium\_name> |

where <medium\_name> is the medium that you previously assigned for the backup operation. For example, you can select the following media from the [database configuration examples](plugins_sap_maxdb_deploy_configure_db.md):

* VEEAMDATA is a media for a full data backup
* VEEAMPAGES is a media for an incremental data backup
* VEEAMLOG is a media for an interactive log backup

For example:

|  |
| --- |
| backup\_start VEEAMDATA |

To learn more about the backup\_start command, see [SAP MaxDB documentation](https://maxdb.sap.com/doc/7_7/39/e89fe68c0f46ad888b055a9f11cb23/frameset.htm).


