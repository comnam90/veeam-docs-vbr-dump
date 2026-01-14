---
title: "SAP on Oracle Backup Using Backint"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_brbackup.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# SAP on Oracle Backup Using Backint

In this article

Veeam Plug-In for SAP on Oracle integrates with the BRBACKUP tool and transfers backup files to backup repositories connected to Veeam Backup & Replication. The backup process itself is performed by the BRBACKUP tool. To perform the backup you can use BR\*TOOLS or BR\*TOOLS Studio.

For details on how the backup is performed, see [How Veeam Plug-In for SAP on Oracle Works](hiw_sap_orcl_plugin.md).

To back up Oracle databases, you can use the interactive wizard of BRTOOLS or you can directly run the backup command using BRBACKUP. When you back up the database using the BRBACKUP tool, you must specify the path to the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) as the argument for the -p (-profile) parameter.

|  |
| --- |
| Note |
| You can make incremental backups only with the rman\_util parameter. For details, see [this SAP article](https://help.sap.com/doc/saphelp_nw74/7.4.16/en-us/47/3b8f17fae93423e10000000a1553f6/content.htm?no_cache=true). To learn how to perform an incremental backup, see [Incremental Backup](sap_orcl_incr.md). |

Examples

The following examples are only for demonstration purposes. To see the description of all BRBACKUP parameters, see the [Backing Up the Database with BR\*Tools for Oracle DBA Guide](https://help.sap.com/doc/saphelp_nwpi71/7.1/de-DE/47/13c2db79711dcde10000000a155369/content.htm?no_cache=true).

* [Full Backup](sap_orcl_backint_full.md)
* [Redo Logs Backup](sap_orcl_logs.md)

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
