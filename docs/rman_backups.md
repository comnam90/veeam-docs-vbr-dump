---
title: "Restoring from RMAN Plug-in Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_backups.html"
last_updated: "11/3/2025"
product_version: "13.0.1.1071"
---

# Restoring from RMAN Plug-in Backups

In this article

This section explains how to restore Oracle data from backups created with Veeam Plug-In for Oracle RMAN. For more information, see [Veeam Plug-In for Oracle RMAN](rman_plugin.md).

Before you restore data from RMAN plug-in backups, make sure that your infrastructure is set up properly. In particular, note that when you restore from an RMAN plug-in backup to another server and Veeam Plug-In for Oracle RMAN on the target server does not have access to the source backup, you must configure the plug-in authentication settings. For more information, see [Considerations and Limitations](veor_considerations.md#restore-rman).

To restore RMAN plug-in backups, do the following:

1. [Launch the Restore wizard](rman_restore_wizard.md).
2. [Specify the recovery type](rman_recovery_type.md).
3. [Specify the target server](rman_target.md).
4. [Specify Oracle settings](rman_oracle_settings.md).
5. [Specify home user password](specify_home_user_password.md).
6. [Specify SYS user password](rman_sys_user_password.md).
7. [Specify point in time](rman_pit.md).
8. [Specify database files location](rman_file_location.md).
9. [Configure channel allocation](rman_channel_allocation.md).
10. [Review the restore summary](veor_restore_rman_summary.md).

Page updated 11/3/2025

Page content applies to build 13.0.1.1071
