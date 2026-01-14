---
title: "VBREPPermission"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbreppermission.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBREPPermission

In this article

Contains user access permissions for backup repositories used by Veeam Agent for Microsoft Windows backup jobs.

Properties

| Property | Type | Description |
| --- | --- | --- |
| RepositoryId | GUID | ID of backup repository used to store Veeam Agent for Microsoft Windows backups. |
| PermissionType | [VBREPPermissionType](enums.md#VBREPPermissionType) | Repository permission type. |
| Users | string[] | Users or user groups allowed to use the repository. |
| IsEncryptionEnabled | bool | Indicates if the Veeam Agent for Microsoft Windows backup data written to the repository is encrypted (TRUE) or not (FALSE). |
| EncryptionKey | [VBREncryptionKey](pscryptokey.md) | Encryption key used for encryption. |

Related Commands

* [Get-VBREPPermission](get-vbreppermission.md)
* [Set-VBREPPermission](set-vbreppermission.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
