---
title: "Get-VBRRepositoryMountServerOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrepositorymountserveroptions.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Get-VBRRepositoryMountServerOptions

In this article

Short Description

Returns settings of a mount server associated with a backup repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRRepositoryMountServerOptions -Repository <CBackupRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the [VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md) object. This object contains settings of a mount server associated with a backup repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the backup repository with which the mount server is associated. The cmdlet will return the settings of this mount server. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md)

Examplesv

Getting Mount Server Settings for Backup Repository

This example shows how to return settings of the mount server associated with the Linux-XFS repository.

|  |
| --- |
| $repository = Get-VBRBackupRepository -Name "Linux-XFS Repository"  $mount\_server\_settings = Get-VBRRepositoryMountServerOptions -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the Get-VBRRepositoryMountServerOptions cmdlet. Set the $repository variable as the Repository parameter value. Save the result to the $mount\_server\_settings variable to use it with other cmdlets.

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 9/5/2025

Page content applies to build 13.0.1.1071
