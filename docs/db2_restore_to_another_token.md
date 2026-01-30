---
title: "Restore to Another Server Using Recovery Token"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore_to_another_token.html"
last_updated: "10/23/2024"
product_version: "13.0.1.1071"
---

# Restore to Another Server Using Recovery Token


You can restore a database to another server using a recovery token generated in Veeam Backup & Replication and provided to you by a backup administrator.

To restore database, do the following steps:

1. Start the restore operation with the following command:

|  |
| --- |
| /opt/veeam/VeeamPluginforDB2/DB2ConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using a recovery token, type 3:

|  |
| --- |
| Select authentication type or disable the functionality: |

1. Veeam Plug-In will display the fingerprint of the Veeam Backup & Replication server and prompt you to provide a recovery token:

|  |
| --- |
| Veeam Backup & Replication server fingerprint: CA4F820F164C02A9AAC75562FC35330A93CDAA3C. Continue? (y/n) : y Enter recovery token: |

1. Veeam Plug-In will display backups for which the recovery token was generated. Select the necessary backup:

|  |
| --- |
| Select backup to be used: 1. Backup1 2. Backup2 3. Backup3 Enter backup number: 3 The selected backup [Backup3] will be used for all restore operations. |

1. Depending on the name of the target instance, perform one of the following operations:

* If you restore to to another instance with the same name as the backed-up instance, continue the restore operation in the same way you restore to the original server. For details, see [Restore to Original Server](db2_restore_to_original.md).

* If you plan to restore to another instance with a name that is different from the backed-up instance, see [Restore to Instance with Different Name](db2_restore_to_server_with_different_name.md).


