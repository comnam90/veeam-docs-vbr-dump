---
title: "Stop-VBREntraIDTenantBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrentraidtenantbackupjob.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# Stop-VBREntraIDTenantBackupJob

In this article

Short Description

Stops running backup jobs that protect Microsoft Entra ID tenants.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBREntraIDTenantBackupJob -Job <VBREntraIDTenantBackupJob[]> [-RunAsync] [-Gracefully] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet stops Entra ID tenant backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of tenant backup jobs that you want to stop. | Accepts the VBREntraIDTenantBackupJob[] object. To get this object, run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| RunAsync | Defines that the command will return immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Gracefully | Defines that the cmdlet will stop the job gracefully. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Entra ID Tenant Backup Job

This example shows how to stop the Tenant Backup backup job.

|  |
| --- |
| $backupJob = Get-VBREntraIDTenantBackupJob -Name "Tenant Backup"  Stop-VBREntraIDTenantBackupJob -Job $backupJob -Gracefully -RunAsync |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $backupJob variable.
2. Run the Stop-VBREntraIDTenantBackupJob cmdlet. Set the $backupJob variable as the Job parameter value. Provide the Gracefully and RunAsync parameters.

Related Commands

[Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md)

Page updated 1/9/2025

Page content applies to build 13.0.1.1071
