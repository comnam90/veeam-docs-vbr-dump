---
title: "Audit Logs Location"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/audit_logs_location.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Audit Logs Location


Veeam Backup & Replication logs activities during File-Level Restore sessions involving backups, replicas and unstructured data backups. The results are stored in form of .csv files that are called audit logs. For more information about log files, see [Managing Logs](logging.md).

In Audit Logs Location field, you can specify folder where the audit logs will be stored. By default, log files are stored in the following folders: %ProgramData%\Veeam\Backup\Audit (for Veeam Backup & Replication on Microsoft Windows) and var\log\Backup\Audit (for Veeam Backup & Replication on Linux). You can also specify an SMB (CIFS) folder.

|  |
| --- |
| Important |
| Storing audit logs on WORM tapes is not supported. Storing audit logs on WORM storage is supported without log compression. This type of storage prevents the data from being deleted or modified. Thus, raw audit logs cannot be deleted after creating compressed files. |

If you use an SMB (CIFS) folder, the service account used for Veeam Backup Service on the machine with Veeam Backup & Replication must have access to that SMB (CIFS) folder. By default, this is the LocalSystem account, so you will need to grant write access to the VBR Server Active Directory computer account.

By default, older audit logs are compressed automatically. To perform this operation, the service account under which Veeam Backup Service runs must have modify permissions on the target folder. If you do not want to compress older audit logs, clear the Compress older audit logs automatically check box.

![Audit Logs Location](images/audit_logs.webp)


