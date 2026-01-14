---
title: "Remove-VBRApplicationBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrapplicationbackupjob.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRApplicationBackupJob

In this article

Short Description

Removes application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRApplicationBackupJob -Job <VBRApplicationBackupJobBase[]>  [<CommonParameters>] |

Detailed Description

This cmdlet removes application backup policies from Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an application backup policy that you want to remove. | Accepts the VBRApplicationBackupJobBase[] object. To get this object, run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Application Backup Policies

This cmdlet shows how to remove the DbsSrv2049 application backup policy from Veeam Backup & Replication infrastructure.

|  |
| --- |
| $job = Get-VBRApplicationBackupJob -Name "DbsSrv2049"  Remove-VBRApplicationBackupJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Remove-VBRApplicationBackupJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md)

Page updated 7/11/2024

Page content applies to build 13.0.1.1071
