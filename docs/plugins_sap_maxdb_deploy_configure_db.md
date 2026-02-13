---
title: "Configuring Database"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_configure_db.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Configuring Database


To back up SAP MaxDB database using Veeam Plug-In, you must configure one or more backup mediums for each database that you want to protect. Also, you must configure the maximum number of backup media to allow multiple mediums to be used in parallel during a single backup operation.

To configure backup media, run the following operations:

1. Enter Database Manager CLI:

|  |
| --- |
| /opt/sdb/programs/bin/dbmcli -uUTL -d <database> -u <login>,<password> |

where:

* <database> is the database name
* <user> is the name of the database user with administrator rights
* <password> is the password of the database user with administrator rights

For example:

|  |
| --- |
| /opt/sdb/programs/bin/dbmcli -uUTL -d MAXDB1 -u DBADMIN,SECRET |

1. Assign the maximum number of backup mediums for backup and restore operations:

|  |
| --- |
| param\_put -permanent MaxBackupMedia <N> |

where <N> is the maximum number of mediums that can operate in parallel during backup and restore processes.

For example:

|  |
| --- |
| param\_put -permanent MaxBackupMedia 4 |

1. To apply an updated number of backup mediums, restart the database:

|  |
| --- |
| db\_offline  db\_online |

1. Assign backup mediums using the medium\_put command. Veeam Plug-In requires separate backup media for each type of backups:

* Full backup (DATA)
* Incremental backup (PAGES)
* Log backup (LOG)

To learn more about the medium\_put command syntax, see [SAP MaxDB documentation](https://maxdb.sap.com/doc/7_7/45/1125da4d9e7307e10000000a1553f7/content.htm).

For example:

In this example, the following backup mediums are assigned:

* 4 media for the full backup
* 4 media for the incremental backup
* 1 medium for the log backup

|  |
| --- |
| medium\_put VEEAMDATA\pipe1 /tmp/MAXDB1/compipe1 PIPE DATA 0 8 NO NO / BACK |

1. Optionally, you can display all assigned backup mediums using the medium\_getall command:

|  |
| --- |
| medium\_getall |


