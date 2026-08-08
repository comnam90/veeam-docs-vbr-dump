---
title: "New-VBRKerberosPermission"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrkerberospermission.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRKerberosPermission


Short Description

Creates a new permission to access an application backup repository NFS share with Kerberos credentials.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRKerberosPermission -Username <String> -Mode {Read | ReadWrite} [-Description <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new permission to access the NFS share of an application backup repository with Kerberos credentials.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Username | Specifies the name of the user that you want to grant access to the NFS share. | String | True | Named | False |
| Mode | Specifies the set of actions the permission allows:   * Read * ReadWrite | VBRPermissionMode | True | Named | False |
| Description | Specifies the description for the Kerberos permission. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRApplicationBackupRepositoryKerberosPermission](vbrapplicationbackuprepositorykerberospermission.md) object that contains information about the Kerberos permission for the application backup repository NFS share.

Examples

Creating Kerberos Permission to Access NFS Share

This example shows how to create a read/write Kerberos permission for the DOMAIN\BackupUser account to access the NFS share of an application backup repository.

|  |
| --- |
| $permission = New-VBRKerberosPermission -Username "DOMAIN\BackupUser" -Mode ReadWrite -Description "Kerberos permission for backup access" |

Page updated 2026-06-04

