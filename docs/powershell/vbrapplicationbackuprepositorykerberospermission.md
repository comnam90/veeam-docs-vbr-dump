---
title: "VBRApplicationBackupRepositoryKerberosPermission"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationbackuprepositorykerberospermission.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRApplicationBackupRepositoryKerberosPermission


Contains Kerberos permission settings for a user account to access the NFS share of an application backup repository.

VBRApplicationBackupRepositoryKerberosPermission

| Property | Type | Description |
| Description | String | Specifies the description for the Kerberos permission. |
| Mode | VBRPermissionMode | Specifies the permissions granted to the user account. Accepted values:   * Read — grants read-only access. * ReadWrite — grants read and write access. |
| Username | String | Specifies the name of the user account. |

Related Commands

[New-VBRKerberosPermission](new-vbrkerberospermission.md)

Page updated 2026-05-28

