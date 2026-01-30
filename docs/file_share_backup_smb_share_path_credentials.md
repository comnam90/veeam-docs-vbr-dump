---
title: "Step 2. Specify Path to SMB File Share and Access Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_backup_smb_share_path_credentials.html"
last_updated: "11/1/2023"
product_version: "13.0.1.1071"
---

# Step 2. Specify Path to SMB File Share and Access Credentials


At the SMB File Share step of the wizard, specify access settings for the SMB file share:

1. In the SMB server of file share field, specify the path to an SMB file share in the \\server\folder format. You can specify the IPv4 or IPv6 address of the server. Note that you can use IPv6 addresses only if IPv6 communication is enabled as described in the [IPv6 Support](https://helpcenter.veeam.com/docs/vbr/userguide/ipv6.html?ver=13) section.

You can add the root server folder in the \\server format to protect all SMB file shares residing on this server. After that, create a single file backup job to protect the added server, as described in the [Creating File Backup Jobs](https://helpcenter.veeam.com/docs/vbr/userguide/file_share_backup_job.html?ver=13) section. Then all SMB file shares added on this server will be automatically processed with the file backup job and protected. If you previously had several separate non-root shared folders residing on the same server and want to switch to using a single root shared folder to cover the same shares, you do not have to run full backups to update data of protected shares. Instead, you can convert existing backups and update existing file backup jobs to protect single root shared folders comprising all other non-root shared folders residing on the same server. To learn more about the conversion, see the [Converting Backups from Non-Root to Root Shared Folders](https://helpcenter.veeam.com/docs/vbr/userguide/convert_backups_nonroot_to_root.html?ver=13) section. Perform the conversion with extreme caution.

1. If you must specify user credentials to access the shared folder, select the This share requires access credentials check box. From the Credentials drop-down list, select a credentials record for a user account that has Full Control permissions on the shared folder.

To access the SMB share, you must use an account that meets either of the following requirements:

* If you plan to back up the share, you can use an account with read-only permissions.
* If you plan to back up the share and restore files to it, use an account with read/write permissions.

If you have not set up credentials beforehand, click the Manage accounts link at the bottom of the list or click Add on the right to add the credentials. For more information, see the [Managing Credentials](https://helpcenter.veeam.com/docs/vbr/userguide/managing_credentials.html?ver=13) section.

|  |
| --- |
| Note |
| If the This share requires access credentials check box is not selected, Veeam Backup & Replication uses the computer account of the proxy server to access the file share. |

![Step 2. Specify Path to SMB File Share and Access Credentials](images/smb_file_share_wizard_path_to_smb.webp "Specify Path to SMB File Share and Access Credentials")


