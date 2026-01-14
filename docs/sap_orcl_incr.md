---
title: "Incremental Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_incr.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Incremental Backup

In this article

You can perform an incremental backup by using the BRBACKUP command with the rman\_util parameter. An incremental backup contains the changed data from the last full backup. Incremental backups use less media and resources than full backups.

Example: Performing Incremental Backup in Online Mode

|  |
| --- |
| brbackup -p $Oracle\_HOME/dbs/veeam\_initSID.sap -t online\_cons -d rman\_util -m incr -u <user>/<password> |

Run the brbackup command with the following parameters:

1. Specify the path to the initialization profile file ($Oracle\_HOME/dbs/veeam\_initSID.sap) as the argument for the -p (-profile) parameter.
2. Specify online\_cons as the argument for the -t (-type) parameter. With this option, BRBACKUP backs up the database in the online state. Also, BRBACKUP keeps the database open during the backup. If offline redo log files are generated during the backup, BRBACKUP backs up them to the same backup file.
3. Specify rman\_util as the argument for the -d (-device) parameter. This option defines that the backup will be performed using Oracle RMAN.
4. Set incr as the argument for the -m (-mode) parameter.
5. Specify credentials that will be used to connect to the database as the argument for the -u (-user) parameter. For details, see [this SAP article](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/3ef1b95cacbf4f77a066797285371bb9/472032246a5c2c7de10000000a114a6b.html).

To see all brbackup command options, see the [Command Options for BRBACKUP](https://help.sap.com/docs/SAP_NETWEAVER_DBOS/3ef1b95cacbf4f77a066797285371bb9/46e7e24fdcba3c1de10000000a155369.html) section in the SAP Database Guide: Oracle.

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
