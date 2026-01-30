---
title: "Restore to Another Server Using Configured Authentication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_another_auth.html"
last_updated: "4/2/2024"
product_version: "13.0.1.1071"
---

# Restore to Another Server Using Configured Authentication


You can restore a database to another server using an account and authentication method that were specified in the Veeam Plug-In settings during the [Veeam Plug-In configuring](db2_configure.md) process.

To restore database, do the following steps:

1. Start the restore operation with the following command:

|  |
| --- |
| /opt/veeam/VeeamPluginforDB2/DB2ConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using the authentication method that was specified during the Veeam Plug-In configuration process, type 1:

|  |
| --- |
| Select authentication type or disable the functionality: |

1. Veeam Plug-In will display backups available for restore under the user account specified in the Veeam Plug-In configuration. For the user account with a security certificate, Veeam Plug-In displays backups created under this user account.

Select a backup to start the restore process:

|  |
| --- |
| Select backup to be used: 1. Backup1 2. Backup2 3. Backup3 Enter backup number: 3 The selected backup [Backup3] will be used for all restore operations. |

1. Depending on the name of the target instance, perform one of the following operations:

* If you restore to another instance with the same name as the backed-up instance, continue the restore operation in the same way you restore to the original server. For details, see [Restore to Original Server](db2_restore_to_original.md).

* If you plan to restore to another instance with a name that is different from the backed-up instance, see [Restore to Instance with Different Name](db2_restore_to_server_with_different_name.md).


