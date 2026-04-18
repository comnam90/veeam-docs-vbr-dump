---
title: "Restore Oracle Databases"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_sap_orcl.html"
last_updated: "4/16/2026"
product_version: "13.0.1.2067"
---

# Restore Oracle Databases


Veeam Plug-In for SAP on Oracle allows you to restore databases using the BRRESTORE tool functionality. When you launch the restore, BRRESTORE restores the selected database from backup files stored on the backup repository.

By default, BRRESTORE uses the initSID.sap initialization profile. Thus, you must specify the -p $Oracle\_HOME/dbs/veeam\_initSID.sap parameter in the restore commands.

For details on all restore options, see [this SAP article](https://help.sap.com/doc/saphelp_nwpi71/7.1/en-US/46/bafec999701515e10000000a114a6b/frameset.htm).

Example: Performing Full Restore of SAP on Oracle Database

|  |
| --- |
| brrestore -d util\_file -p $Oracle\_HOME/dbs/veeam\_initSID.sap -b last -m full |

Run the brrestore command with the following parameters:

1. Depending on which backup you want to restore from, use the util\_file or rman\_util option as the argument for the -d (-device) parameter:

* If the backup was created by SAP Backint, use util\_file.
* If the backup was created by RMAN, use rman\_util.

1. If you use rman\_util, you must specify the ID of the backup you want to restore from in the initialization profile file. To do so, open the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) and specify the backup ID as the parameter for the rman\_send command:

|  |
| --- |
| rman\_send = "srcBackup=<backup\_ID>'" |

where <backup\_ID> is the ID of the backup you want to restore from.

To obtain a backup ID, do the following:

1. Specify an authentication method to access the backup created for the original server. For details, see [Specifying Authentication Settings](https://helpcenter.veeam.com/archive/backup/120/plugins/restore_other_server_rman.html#auth).
2. Select the backup from which you want to restore a database. For details, see [Selecting Backup](https://helpcenter.veeam.com/archive/backup/120/plugins/restore_other_server_rman.html#backup).

For example:

|  |
| --- |
| rman\_send = "'srcBackup=665ff3d5-d575-5555-bcf5-b1d369bdf41b'" |

After the restore, make sure to delete the rman\_send command. Otherwise, all subsequent backup and restore operations will use the specified backup as their source.

1. Specify the path to the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) as the argument for the -p (-profile) parameter.

1. Specify last as the argument for the -b (-backup) parameter. With this option, BRRESTORE uses the last successful database backup for the restore.
2. Specify full as the argument for the -m (-mode) parameter. With this option, BRRESTORE performs restore of files in all tablespaces, control files and redo log files.


