---
title: "Restore to Another Server Using Credentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_another_creds.html"
last_updated: "9/3/2024"
product_version: "13.0.1.1071"
---

# Restore to Another Server Using Credentials

In this article

To restore a database to another server, you can specify credentials of a user account under which the backup was created.

To restore database, do the following steps:

1. Start the restore operation with the following command:

|  |
| --- |
| /opt/veeam/VeeamPluginforDB2/DB2ConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using credentials of the account under which the backup was created, type 2:

|  |
| --- |
| Select authentication type or disable the functionality: |

1. Veeam Plug-In will prompt you to provide credentials of the user account that under which the backup was created. Enter a user name and password of the account:

|  |
| --- |
| Enter username: Enter password for <username>: |

1. Depending on the name of the target instane, perform one of the following operations:

* If you restore to to another instance with the same name as the backed-up instance, continue the restore operation in the same way you restore to the original server. For details, see [Restore to Original Server](db2_restore_to_original.md).

* If you plan to restore to another instance with a name that is different from the backed-up instance, see [Restore to Instance with Different Name](db2_restore_to_server_with_different_name.md).

Page updated 9/3/2024

Page content applies to build 13.0.1.1071
