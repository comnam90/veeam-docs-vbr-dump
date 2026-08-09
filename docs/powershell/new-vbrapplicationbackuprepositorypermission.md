---
title: "New-VBRApplicationBackupRepositoryPermission"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrapplicationbackuprepositorypermission.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRApplicationBackupRepositoryPermission


Short Description

Creates a new permission for hosts to access an application backup repository NFS share.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRApplicationBackupRepositoryPermission -Mode {Read | ReadWrite} -ServerName <String>  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new permission for hosts to access the NFS share of an application backup repository.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Mode | Specifies the set of actions the permission allows:   * Read * ReadWrite | VBRPermissionMode | True | Named | False |
| ServerName | Specifies the host's DNS name or IP mask. The host will be given the permission to access the NFS share. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRApplicationBackupRepositoryPermission](vbrapplicationbackuprepositorypermission.md) object that contains information about the permission for the application backup repository NFS share.

Examples

Creating Permission Settings to Access NFS Share

This command creates new read/write permission settings for the 172.24.26.132 host to access the NFS share of an application backup repository.

|  |
| --- |
| $permission = New-VBRApplicationBackupRepositoryPermission -Mode ReadWrite -ServerName 172.24.26.132 |

Page updated 2026-06-08

