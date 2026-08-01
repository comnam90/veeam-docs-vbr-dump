---
title: "Restoring Configuration Data Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuration_restore_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring Configuration Data Using Web UI


To restore the configuration database of a backup appliance using the appliance Web UI, do the following:

1. [Launch the Configuration Restore wizard](azure_configuration_restore_ui_wizard.md).
2. [Choose a backup file](azure_configuration_restore_ui_file.md).
3. [Review the backup file info](azure_configuration_restore_ui_info.md).
4. [Choose restore options](azure_configuration_restore_ui_options.md).
5. [Track the restore progress](azure_configuration_restore_ui_progress.md).
6. [View the results of verification steps](azure_configuration_restore_ui_check.md).
7. [Finish working with the wizard](azure_configuration_restore_ui_finish.md).

|  |
| --- |
| Important |
| * Before you start the restore process, stop all policies that are currently running.  * If the backup appliance to which you plan to restore the configuration database is managed by a Veeam Backup & Replication server, you will not be able to restore the configuration of Veeam Backup for Microsoft Azure from the Web UI. In this case, you can perform configuration restore using the Veeam Backup & Replication console as described in section [Restoring Configuration Data Using Console](azure_configuration_restore_console.md). * If the backup appliance whose configuration database you plan to restore used the Azure Service Bus messaging service, you must switch to the Azure Queue Storage service immediately after the restore operation is complete. For more information, see [Configuring Deployment Mode](azure_deployment_mode.md). |

After Veeam Backup for Microsoft Azure performs configuration restore, it rescans the whole infrastructure to detect obsolete snapshots. These snapshots are then removed from the configuration database according to the specified [global retention settings](azure_configuring_global_retention.md).

Page updated 2026-07-01

