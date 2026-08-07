---
title: "Remove-VBRApplicationBackupRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrapplicationbackuprepository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Remove-VBRApplicationBackupRepository


Short Description

Removes an application backup repository from the backup infrastructure.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRApplicationBackupRepository -Repository <VBRApplicationBackupRepository[]> [-RemoveData] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to remove an application backup repository from the backup infrastructure.

By default, when you remove an application backup repository, the NFS share will be unmounted, but the user data and the snapshot restore points will remain on disk. To remove the data on disk, use the RemoveData parameter.

When Veeam Backup & Replication unassigns the repository role from the server, it is no longer used as an application backup repository. The actual server remains added to the backup infrastructure.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Repository | Specifies an array of application backup repositories you want to remove. | Accepts the [VBRApplicationBackupRepository](vbrapplicationbackuprepository.md)[] object. To get this object, run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. | True | Named | True |
| RemoveData | Defines that the user data and the snapshot restore points stored in the repository will be deleted. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will remove an application backup repository and will not show up any warnings or notifications. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing Backup Repository

This example shows how to remove the application backup repository named Oracle FRA Repository. The data stored in the repository will remain on disk.

|  |
| --- |
| $repository = Get-VBRApplicationBackupRepository -Name "Oracle FRA Repository"  Remove-VBRApplicationBackupRepository -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the Remove-VBRApplicationBackupRepository cmdlet. Set the $repository variable as the Repository parameter value.

Related Commands

[Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md)

Page updated 2026-05-29

