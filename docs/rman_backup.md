---
title: "Oracle RMAN Full Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_backup.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Oracle RMAN Full Backup


After you configure Veeam Plug-In, you can use the Oracle RMAN functionality to back up databases. Veeam Plug-In will automatically transfer the backup files to the Veeam backup repository. For more information about configuring Veeam Plug-In, see [Configuring Veeam Plug-In for Oracle RMAN](configuring_rman_plugin.md).

You can create a consistent backup of Oracle databases in the ARCHIVELOG mode and in the NOARCHIVELOG mode. For details on the backup process in different modes, see [this Oracle article](https://docs.oracle.com/cd/B28359_01/server.111/b28310/archredo002.htm#ADMIN11330).

|  |
| --- |
| Note |
| The examples given below are for demonstration purposes only. The backup process is performed on the Oracle RMAN side. Consider configuring required RMAN-specific parameters that may affect the backup process. For details on the backup functionality of Oracle RMAN, see [this Oracle article](https://docs.oracle.com/cd/E11882_01/backup.112/e10642/rcmbckba.htm). |

Consistent Backup of Oracle Database in ARCHIVELOG Mode

To create a consistent backup of an Oracle database and redo logs in the ARCHIVELOG mode, run the following script. In this example, Oracle RMAN will back up the entire database and available archived redo logs. The current online redo log will be archived to make sure all redo changes are transferred to the archived redo log chain. In the ARCHIVELOG mode, there will be no downtime as you do not have to shut down the database.

|  |
| --- |
| RUN {  BACKUP DATABASE PLUS ARCHIVELOG;  }  EXIT; |

Consistent Backup of Oracle Database in NOARCHIVELOG Mode

To create a consistent backup of an Oracle database operating in the NOARCHIVELOG mode, start the Oracle RMAN console and run the following script. In this example, the database instance will be started after the backup process is complete. Note that the database will be unavailable during the backup.

|  |
| --- |
| RUN {  SHUTDOWN TRANSACTIONAL;  STARTUP MOUNT;  BACKUP DATABASE;  STARTUP;  }  EXIT; |


