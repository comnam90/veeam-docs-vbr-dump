---
title: "Disable-VBRApplicationBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrapplicationbackupjob.html"
last_updated: "7/11/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRApplicationBackupJob

In this article

Short Description

Disables application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRApplicationBackupJob -Job <VBRApplicationBackupJobBase[]> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet disables application backup policies.

Run the [Enable-VBRApplicationBackupJob](enable-vbrapplicationbackupjob.md) cmdlet to enable application backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an application backup policy that you want to disable. | Accepts the VBRApplicationBackupJobBase[] object. To get this object, run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRApplicationBackupJobBase[] object that contains settings of disabled application backup policies.

Examples

Disabling Application Backup Policy

This example shows how to disable the DbsSrv2049 application backup policy.

|  |
| --- |
| $job = Get-VBRApplicationBackupJob -Name "DbsSrv2049"  Disable-VBRApplicationBackupJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Disable-VBRApplicationBackupJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md)

Page updated 7/11/2024

Page content applies to build 13.0.1.1071
