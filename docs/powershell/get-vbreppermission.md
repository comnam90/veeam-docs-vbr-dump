---
title: "Get-VBREPPermission"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbreppermission.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBREPPermission


Short Description

Returns user access permissions for backup repositories for Veeam Agent or Veeam Plug-in operating in the standalone mode.

Syntax

|  |
| --- |
| Get-VBREPPermission -Repository <CBackupRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet returns user access permissions for a backup repository that is used as a target by Veeam Agent or Veeam Plug-in operating in the standalone mode.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the backup repository. The cmdlet will return the permissions for these repositories. | Accepts string (repository name) or the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBREPPermission](vbreppermission.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Repository Permissions [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get the repository permissions using a variable.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "WinLocal"  Get-VBREPPermission -Repository $repository  RepositoryId        : 88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec PermissionType      : Everyone Users               : {} IsEncryptionEnabled : False EncryptionKey       : |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 2. Run the Get-VBREPPermission cmdlet. Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Repository Permissions [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get the repository permissions using a pipeline.  |  | | --- | | Get-VBRBackupRepository -Name "WinLocal" | Get-VBREPPermission  RepositoryId        : 88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec PermissionType      : Everyone Users               : {} IsEncryptionEnabled : False EncryptionKey       : |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBREPPermission cmdlet. |

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)


