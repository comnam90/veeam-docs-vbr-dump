---
title: "Stop-VBRApplicationBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrapplicationbackupjob.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRApplicationBackupJob

In this article

Short Description

Stops application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRApplicationBackupJob -Job <VBRApplicationBackupJobBase[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet stops application backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an application backup policy that you want to stop. | Accepts the VBRApplicationBackupJobBase[] object. To get this object, run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Application Backup Policies

This example shows how to stop the application backup policy.

|  |
| --- |
| $job = Get-VBRApplicationBackupJob -Name "DbsSrv2049"  Stop-VBRApplicationBackupJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Stop-VBRApplicationBackupJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md)

Page updated 7/11/2024

Page content applies to build 13.0.1.1071
