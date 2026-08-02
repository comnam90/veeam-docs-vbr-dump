---
title: "Shared Folder Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_win_target_share_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Shared Folder Settings


At the Shared Folder step of the wizard, specify shared folder settings:

1. In the Path to shared folder field, type a UNC name of the SMB (CIFS) network shared folder in which you want to store backup files. Keep in mind that the UNC name always starts with two back slashes (\\).
2. If the SMB network shared folder requires authentication, select the This file share requires access credentials check box and select from the list a user account that has access permissions on this shared folder. If you have not set up credentials beforehand, click the Manage Accounts link or click Add on the right to add credentials.

The user name can be specified in the following formats:

* DNS.DOMAIN.NAME\USERNAME
* USERNAME@DNS.DOMAIN.NAME
* HOSTNAME\USERNAME — if you use Veeam Backup & Replication on Microsoft Windows
* DOMAIN\USERNAME — if you use Veeam Backup & Replication on Microsoft Windows

If you do not select the This file share requires access credentials check box, Veeam Agent for Microsoft Windows will connect to the shared folder using the NT AUTHORITY\SYSTEM account of the computer where the product is installed. You can use this scenario if the Veeam Agent computer is joined to the Active Directory domain. In this case, you can simply grant Full Control access on the shared folder and underlying file system to the computer account (DOMAIN\COMPUTERNAME$).

1. In the Keep backups for field, specify the number of days for which you want to store backup files in the target location. After this period is over, Veeam Agent will remove from the backup chain any restore points that are older than the specified retention period. By default, Veeam Agent keeps backup files for 7 days, excluding days with no backup. To learn more, see [Short-Term Retention Policy](agents_retention.md).
2. To use the GFS (Grandfather-Father-Son) retention scheme, next to Keep certain full backups longer for archival purposes, click the current setting summary. In the Configure GFS window, specify how weekly, monthly and yearly full backups must be retained. To learn more, see [Long-Term Retention Policy (GFS)](gfs_retention_policy.md).

Keep in mind that to use the GFS retention policy, you must set Veeam Agent to create full backups. To learn more, see [Backup Settings](agent_policy_advanced_backup_web.md).

1. Click Configure advanced settings to specify advanced settings for the backup policy. To learn more, see [Specify Advanced Backup Settings](agent_policy_win_advanced_web.md).

[![Specify Shared Folder Settings](images/agent_policy_share_web.webp)](images/agent_policy_share_web.webp "Specify Shared Folder Settings")

Page updated 2026-07-16

