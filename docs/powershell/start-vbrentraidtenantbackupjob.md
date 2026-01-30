---
title: "Start-VBREntraIDTenantBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrentraidtenantbackupjob.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Start-VBREntraIDTenantBackupJob


Short Description

Starts Entra ID tenant backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBREntraIDTenantBackupJob [-Job] <VBREntraIDTenantBackupJob[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts backup jobs that protect Microsoft Entra ID tenants.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of tenant backup jobs that you want to start. | Accepts the VBREntraIDTenantBackupJob[] object. To get this object, run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupSession object that contains information about the job session.

Examples

Starting Entra ID Tenant Backup Job

This example shows how to start the Tenant Backup backup job.

|  |
| --- |
| $backupJob = Get-VBREntraIDTenantBackupJob -Name "Tenant Backup"  Start-VBREntraIDTenantBackupJob -Job $backupJob |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $backupJob variable.
2. Run the Start-VBREntraIDTenantBackupJob cmdlet. Set the $backupJob variable as the Job parameter value.

Related Commands

[Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md)


