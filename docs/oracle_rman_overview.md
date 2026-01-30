---
title: "Overview"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/oracle_rman_overview.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Overview


Veeam Backup & Replication offers two options to protect Oracle databases:

* Using Veeam Backup & Replication or Veeam Agent for Oracle Solaris for image-level backups of Oracle servers.

Veeam Backup & Replication and Veeam Agent for Oracle Solaris perform image-level backup and restore operations of Oracle servers. For example, this may be useful if you do not have Oracle database administrators.

To learn how to use Veeam Backup & Replication to protect Oracle servers, see [Creating Backup Jobs](backup_job.md).

To learn how to use Veeam Agent for Oracle Solaris to protect Oracle servers, see the [Overview](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/about.html?ver=40) section of the Veeam Agent for Oracle Solaris User Guide.

* Using Veeam Plug-In for Oracle RMAN for transactionally-consistent Oracle Recovery Manager (RMAN) based backups of Oracle databases.

Veeam Plug-In uses the backup and restore functionality of RMAN and transfers backups to Veeam backup repositories. Use Veeam Plug-In to back up Oracle databases in the following cases:

* If you want the Oracle database administrator to fully control the backup and recovery processes.
* If you want to use existing Oracle RMAN scripts or external schedulers.
* If you use Real Applications Clusters (Oracle RAC).
* If you use Automatic Storage Management (Oracle ASM) disks on a physical server.

Veeam Plug-In functions as an agent between Oracle RMAN and the Veeam backup repository. With the configured Veeam Plug-In, the default backup device type is changed and gives control over backup media management to Veeam Plug-In. Veeam Plug-In compresses and transfers database backups to a backup repository connected to Veeam Backup & Replication. For details, see [How Veeam Plug-In for Oracle RMAN Works](hiw_rman_plugin.md).

Veeam Plug-In for Oracle RMAN can operate in standalone or managed mode. Depending on the operation mode, Veeam Plug-In has different functionality and limitations. In standalone mode, you can install Veeam Plug-In manually on the computer whose databases you want to protect. Veeam Plug-In in standalone mode uses the Veeam Backup & Replication console to perform backup operations. In managed mode, you can install Veeam Plug-In using the Veeam Backup & Replication console. The Veeam Backup & Replication console automates the operation of Veeam Plug-Ins running on computers in your infrastructure. For details on Veeam Plug-In operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md#modes).

For backup operations, you can use the built-in Oracle RMAN functionality. Veeam Plug-In for Oracle RMAN transfers backup data to the Veeam backup repository and stores the data in the Veeam proprietary format for backups. Veeam Backup & Replication creates a backup job for all backup processes started in Oracle RMAN. Use this job to view the statistics on the backup process, generate backup job reports or disable the backup job. For details on backup operations, see [Data Backup](rman_data_backup.md).

In case of malware activity or unplanned actions, you can perform restore operations based on the backup data transferred by Veeam Plug-In to the Veeam Backup & Replication backup repositories. Use the built-in Oracle RMAN functionality or Veeam Explorer for Oracle to restore databases. Restore processes run on the Oracle side. For details on restore operations with Veeam Plug-In, see [Data Restore](rman_data_restore.md).


