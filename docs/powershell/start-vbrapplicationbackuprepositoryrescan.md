---
title: "Start-VBRApplicationBackupRepositoryRescan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrapplicationbackuprepositoryrescan.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRApplicationBackupRepositoryRescan


Short Description

Rescans an application backup repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRApplicationBackupRepositoryRescan -Repository <VBRApplicationBackupRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans an application backup repository to update the list of snapshots stored in the repository. By default, Veeam Backup & Replication runs the rescan every 24 hours. You can use this cmdlet to start the rescan manually.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Repository | Specifies the application backup repository that you want to rescan. | Accepts the [VBRApplicationBackupRepository](vbrapplicationbackuprepository.md) object. To get this object, run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Rescanning Application Backup Repository

This example shows how to rescan an application backup repository.

|  |
| --- |
| $repo = Get-VBRApplicationBackupRepository -Name "AppBackupRepo01"  Start-VBRApplicationBackupRepositoryRescan -Repository $repo |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repo variable.
2. Run the Start-VBRApplicationBackupRepositoryRescan cmdlet. Set the $repo variable as the Repository parameter value.

Related Commands

[Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md)

Page updated 2026-06-04

