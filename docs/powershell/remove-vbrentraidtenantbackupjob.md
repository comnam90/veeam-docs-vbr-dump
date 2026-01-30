---
title: "Remove-VBREntraIDTenantBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrentraidtenantbackupjob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Remove-VBREntraIDTenantBackupJob


Short Description

Removes backup jobs that protect Microsoft Entra ID tenants.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBREntraIDTenantBackupJob -Job <VBREntraIDTenantBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet removes Entra ID tenant backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of tenant backup jobs that you want to remove. | Accepts the VBREntraIDTenantBackupJob[] object. To get this object, run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Entra ID Tenant Backup Job

This example shows how to remove the Tenant Backup backup job.

|  |
| --- |
| $backupJob = Get-VBREntraIDTenantBackupJob -Name "Tenant Backup"  Remove-VBREntraIDTenantBackupJob -Job $backupJob |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $backupJob variable.
2. Run the Remove-VBREntraIDTenantBackupJob cmdlet. Set the $backupJob variable as the Job parameter value.

Related Commands

[Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md)


