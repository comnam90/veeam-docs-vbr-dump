---
title: "Redo Logs Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_logs.html"
last_updated: "9/3/2024"
product_version: "13.0.1.1071"
---

# Redo Logs Backup


If you want to back up redo log files of Oracle databases separately from the database files, you can use the BRARCHIVE tool. When Veeam Plug-In for SAP on Oracle is configured, the plug-in transfers the redo logs to a backup repository connected to Veeam Backup & Replication.

|  |
| --- |
| Note |
| For redo log backup operations, it is recommended to set 4 or less parallel channels. For details on configuring parallel channels, see [Configuring Parallelism for Redo Logs](sap_orcl_parallelism.md). |

Example: Performing Backup of Archived Redo Logs

To back up redo log files, run the following command.

|  |
| --- |
| brarchive -p $Oracle\_HOME/dbs/veeam\_initSID.sap -save -d util\_file -u <user>/<password> |

1. Specify the path to the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) as the argument for the -p (-profile) parameter.
2. Specify the archive function. The -save function used in this example archives offline redo log files to a repository.
3. Specify util\_file as the argument for the -d (-device) parameter. This option defines that a file-by-file backup will be performed using Veeam Plug-In.
4. Specify credentials that will be used to connect to the database as the argument for the -u (-user) parameter. For details, see [this SAP article](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/3ef1b95cacbf4f77a066797285371bb9/472032246a5c2c7de10000000a114a6b.html).


