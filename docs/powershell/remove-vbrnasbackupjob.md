---
title: "Remove-VBRNASBackupJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrnasbackupjob.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRNASBackupJob (obsolete)

In this article

Short Description

Removes file backup jobs from Veeam Backup & Replication infrastructure.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Remove-VBRUnstructuredBackupJob](remove-vbrunstructuredbackupjob.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRNASBackupJob -Job <VBRNASBackupJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes file backup jobs from Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a file backup job. The cmdlet will remove this job from the Veeam Backup & Replication infrastructure. | Accepts the VBRNASBackupJob[] object. To get this object, run the [Get-VBRNASBackupJob](get-vbrnasbackupjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupJob object that contains settings of file backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing All File Backup Jobs

|  |  |
| --- | --- |
| This example shows how to remove all file backup jobs from the Veeam Backup & Replication infrastructure.  |  | | --- | | $job = Get-VBRNASBackupJob  Remove-VBRNASBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRNASBackupJob](get-vbrnasbackupjob.md) cmdlet. Save the result to the $job variable. 2. Run the Remove-VBRNASBackupJob cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing File Backup Jobs by Name

|  |  |
| --- | --- |
| This example shows how to remove the SMB Job file backup jobs.  |  | | --- | | $job = Get-VBRNASBackupJob -Name "SMB Job"  Remove-VBRNASBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRNASBackupJob](get-vbrnasbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Remove-VBRNASBackupJob cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRNASBackupJob](get-vbrnasbackupjob.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
