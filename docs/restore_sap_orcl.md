---
title: "Restore Oracle Databases"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_sap_orcl.html"
last_updated: "3/14/2024"
product_version: "13.0.1.1071"
---

# Restore Oracle Databases

In this article

Veeam Plug-In for SAP on Oracle allows you to restore databases using the BRRESTORE tool functionality. When you launch the restore, BRRESTORE restores the selected database from backup files stored on the backup repository.

By default, BRRESTORE uses the initSID.sap initialization profile. Thus, you must specify the -p $Oracle\_HOME/dbs/veeam\_initSID.sap parameter in the restore commands.

For details on all restore options, see [this SAP article](https://help.sap.com/doc/saphelp_nwpi71/7.1/en-US/46/bafec999701515e10000000a114a6b/frameset.htm).

Example: Performing Full Restore of SAP on Oracle Database

|  |
| --- |
| brrestore -d util\_file -p $Oracle\_HOME/dbs/veeam\_initSID.sap -b last -m full |

Run the brrestore command with the following parameters:

1. Depending on which backup you want to restore from, use the util\_file or rman\_util option as the argument for the -d (-device) parameter. If the backup was created by Backint, use util\_file. If the backup was created by RMAN, use rman\_util.
2. Specify the path to the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) as the argument for the -p (-profile) parameter.
3. Specify last as the argument for the -b (-backup) parameter. With this option, BRRESTORE uses the last successful database backup for the restore.
4. Specify full as the argument for the -m (-mode) parameter. With this option, BRRESTORE performs restore of files in all tablespaces, control files and redo log files.

Page updated 3/14/2024

Page content applies to build 13.0.1.1071
