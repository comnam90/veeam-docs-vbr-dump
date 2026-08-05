---
title: "Log backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_db2_backup_types_log_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Log backup


Veeam Plug-In for IBM Db2 supports backup and restore operations of archived logs for IBM Db2 databases. Archive logs contain all transactional changes to enable recovery and point-in-time restores. Set the logarchmeth1 parameter during the configuration of Veeam Plug-In for IBM Db2 to specify the log method and storage destination of archive logs.

You can also set the logarchmeth2 parameter in IBM Db2 databases to specify a secondary archive log method or location. Configure this parameter in addition to setting the logarchmeth1 parameter.

There are two approaches for processing archive logs with Veeam Plug-In for IBM Db2:

* Automatic log processing: Veeam Backup & Replication manages archived log processing automatically and transfers the logs to a Veeam backup repository.

Once the primary database archive method is configured with the logarchmeth1 parameter and an online backup is performed, Veeam Plug-In for IBM Db2 automatically processes and transfers archived logs to the selected backup repository. The Veeam Backup & Replication job configuration controls the log backup frequency and retention. For more information on how to set the logarchmeth1 parameter automatically, see [Configuring Plug-In on Microsoft Windows](db2_configure_win.md) and [Configuring Plug-In on Linux and Unix](db2_configure_linux_unix.md#archive_log).

* Manual log processing: IBM Db2 commands allow manual archiving and transferring of logs to a configured destination.

Manual log processing is an optional action available after the setup of Veeam Plug-In for IBM Db2. By default, automatic log processing is always active unless specifically disabled or modified. Manual log backup or intervention may be required in custom configurations or troubleshooting scenarios. You can archive or copy logs manually using IBM Db2 commands. For more information on how to set the logarchmeth1 and logarchmeth2 parameters manually, see [Performing Log Backup](db2_protection_log.md).

Page updated 2026-07-08

