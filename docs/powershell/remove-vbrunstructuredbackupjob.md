---
title: "Remove-VBRUnstructuredBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrunstructuredbackupjob.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRUnstructuredBackupJob

In this article

Short Description

Removes file backup jobs and object storage backup jobs from the backup infrastructure.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRUnstructuredBackupJob -Job <VBRUnstructuredBackupJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes file backup jobs and object storage backup jobs from the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of file backup jobs and object storage backup jobs. The cmdlet will remove these jobs from the backup infrastructure. | Accepts the VBRUnstructuredBackupJob[] object. To get this object, run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing All File Backup and Object Storage Backup Jobs

|  |  |
| --- | --- |
| This example shows how to remove all file backup jobs from the Veeam Backup & Replication infrastructure.  |  | | --- | | $job = Get-VBRUnstructuredBackupJob  Remove-VBRUnstructuredBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Save the result to the $job variable. 2. Run the Remove-VBRUnstructuredBackupJob cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Object Storage Backup Jobs by Name

|  |  |
| --- | --- |
| This example shows how to remove the Azue Job file backup jobs.  |  | | --- | | $job = Get-VBRUnstructuredBackupJob -Name "Azue Job"  Remove-VBRUnstructuredBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Remove-VBRUnstructuredBackupJob cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
