---
title: "Restore to Another Server Using Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_another_creds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restore to Another Server Using Credentials


To restore a database to another server, you can specify credentials of a user account under which the backup was created.

To restore database, do the following steps:

1. Start the restore operation using one of the following commands depending on the OS you are using:

* For Linux or Unix:

|  |
| --- |
| /opt/veeam/VeeamPluginforDB2/DB2ConfigTool --set-backup-for-restore |

* For Microsoft Windows:

|  |
| --- |
| "C:\Program Files\Veeam\VeeamPluginforDB2\DB2ConfigTool.exe" --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using credentials of the account under which the backup was created, type 2:

|  |
| --- |
| Select authentication type or disable the functionality: 0. To disable the functionality 1. Currently set authentication data 2. Credentials 3. Recovery token Enter authentication type number: 2 |

1. Veeam Plug-In will prompt you to provide credentials of the user account that under which the backup was created. Enter a user name and password of the account:

|  |
| --- |
| Enter username: Enter password for <username>: |

1. Depending on the name of the target instance, perform one of the following operations:

* If you restore to another instance with the same name as the backed-up instance, continue the restore operation in the same way you restore to the original server. For details, see [Restore to Original Server](db2_restore_to_original.md).

* If you plan to restore to another instance with a name that is different from the backed-up instance, see [Restore to Instance with Different Name](db2_restore_to_server_with_different_name.md).

Page updated 2026-07-02

