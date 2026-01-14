---
title: "Remove-VBRCloudTenantBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudtenantbackup.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudTenantBackup

In this article

Short Description

Removes selected backups of tenants from disk.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCloudTenantBackup -CloudTenantBackup <VBRCloudTenantBackup[]> [-IncludeGFS] [-RunAsync] [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet removes selected backups of AD tenants and tenants managed by the Service Provider.

If the backups that you plan to remove are associated with an active job, perform the following steps:

1. Before you run this cmdlet, disable the tenant. To do this, run the [Disable-VBRCloudTenant](disable-vbrcloudtenant.md) cmdlet.
2. After the backup removal is finished, enable the tenant. To do this, run the [Enable-VBRCloudTenant](enable-vbrcloudtenant.md) cmdlet.
3. Ask the tenant to rescan the service provider to update the information.

|  |
| --- |
| Important |
| Do not use this cmdlet with immutable backups. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenantBackup | Specifies the array of tenant backups you want to remove. | Accepts the VBRCloudTenantBackup[] object. To get this object, run the [Get-VBRCloudTenantBackup](get-vbrcloudtenantbackup.md) cmdlet. | True | 0 | True (ByValue, |
| IncludeGFS | Defines that the cmdlet will remove backups with GFS flags (weekly, monthly and yearly). | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwichParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Orphaned Backups of Cloud Tenant Account

This example shows how to remove orphaned backups for the ABC Company cloud tenant account.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "ABC Company"  $backupfiles = Get-VBRCloudTenantBackup -All -Tenant $tenant | Where-Object {$\_.IsOrphaned -eq $true}  Remove-VBRCloudTenantBackup -CloudTenantBackup $backupfiles |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Run the [Get-VBRCloudTenantBackup](get-vbrcloudunavailablebackupfile.md) cmdlet. Specify the following settings:

* Provide the All parameter.
* Set the $tenant variable as the Tenant parameter value.
* Pipe the cmdlet output to the Where-Object cmdlet and specify the IsOrphaned value to equal $true.
* Save the result to the $backupfiles variable.

1. Run the Remove-VBRCloudTenantBackup cmdlet. Set the $backupfiles variable as the CloudTenantBackup parameter value.

Related Commands

* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Get-VBRCloudTenantBackup](get-vbrcloudtenantbackup.md)

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
