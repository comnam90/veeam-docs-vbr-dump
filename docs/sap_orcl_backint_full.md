---
title: "Full Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_backint_full.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Full Backup


If you want to create a full backup Oracle databases, you can use the BRBACKUP tool. When Veeam Plug-In for SAP on Oracle is configured, the plug-in transfers database backup files to a backup repository connected to Veeam Backup & Replication.

Example 1. Performing Full Database Backup in Offline Mode

|  |
| --- |
| brbackup -p $Oracle\_HOME/dbs/veeam\_initSID.sap -d util\_file -t offline\_force -m all -u <user>/<password> |

Run the brbackup command with the following parameters:

1. Specify the path to the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) as the argument for the -p (-profile) parameter.
2. Specify util\_file as the argument for the -d (-device) parameter. This option defines that a file-by-file backup will be performed using Veeam Plug-In.
3. Specify offline\_force as the argument for the -t (-type) parameter. With this option, BRBACKUP shuts down the database and performs an offline backup.
4. Specify the argument for the -m (-mode) parameter. With the all argument, BRBACKUP backs up files in all tablespaces, but not the control files and online redo log files. For the full list of arguments for the -mode parameter, see [this SAP article](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/3ef1b95cacbf4f77a066797285371bb9/47206a8c49bd12b6e10000000a1553f7.html).
5. Specify credentials that will be used to connect to the database as the argument for the -u (-user) parameter. For details, see [this SAP article](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/3ef1b95cacbf4f77a066797285371bb9/472032246a5c2c7de10000000a114a6b.html).

Example 2. Performing Full Database Backup in Online Mode

|  |
| --- |
| brbackup -p $Oracle\_HOME/dbs/veeam\_initSID.sap -d util\_file\_online -t online\_cons -m all -u <user>/<password> |

Run the brbackup command with the following parameters:

1. Specify the path to the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) as the argument for the -p (-profile) parameter.
2. Specify util\_file\_online as the argument for the -d (-device) parameter.
3. Specify online\_cons as the argument for the -t (-type) parameter. With this option, BRBACKUP backs up the database in the online state. Also, BRBACKUP keeps the database open during the backup. If offline redo log files are generated during the backup, BRBACKUP backs up them to the same backup file.
4. Specify the argument for the -m (-mode) parameter. With the all argument, BRBACKUP backs up files in all tablespaces, but not the control files and online redo log files. For the full list of arguments for the -mode parameter, see [this SAP article](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/3ef1b95cacbf4f77a066797285371bb9/47206a8c49bd12b6e10000000a1553f7.html).
5. Specify credentials that will be used to connect to the database as the argument for the -u (-user) parameter. For details, see [this SAP article](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/3ef1b95cacbf4f77a066797285371bb9/472032246a5c2c7de10000000a114a6b.html).

|  |
| --- |
| Important |
| When you use BRBACKUP, you must specify the full directory path to the Veeam Plug-In initialization profile file (-p $Oracle\_HOME/dbs/veeam\_initSID.sap). If the profile file is in the default directory, you can specify only the file name. |


