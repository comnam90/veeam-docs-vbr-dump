---
title: "Restore to Original Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_rman.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Restore to Original Server

In this article

Veeam Plug-In for Oracle RMAN allows you to restore databases using built-in Oracle RMAN functionality. When you launch a restore, RMAN restores the necessary database from the backup stored in the Veeam backup repository.

If you want to change the repository or channel settings, you must modify the Veeam Plug-In settings. For details, see [Configuring Veeam Plug-In for Oracle RMAN](configuring_rman_plugin.md).

To restore the Oracle database, you must connect to the database with RMAN and run the restore command. You may need to run additional commands depending on your database infrastructure. Consider configuring required RMAN-specific parameters that may affect the backup process. For details on all restore capabilities of Oracle RMAN, see [this Oracle article](https://docs.oracle.com/en/database/oracle/oracle-database/21/bradv/rman-complete-database-recovery.html#GUID-D908719C-9D46-4084-850C-0F81C25094EB).

|  |
| --- |
| RUN {  SHUTDOWN IMMEDIATE;  }  EXIT; |

|  |
| --- |
| Note |
| If you use the SEND command on the target server to point to the source server, you can run operations like DUPLICATE. For details, see [Restore to Another Server](restore_other_server_rman.md). |

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
