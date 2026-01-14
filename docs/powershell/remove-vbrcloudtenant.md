---
title: "Remove-VBRCloudTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudTenant

In this article

Short Description

Removes cloud tenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Remove-VBRCloudTenant -CloudTenant <IVBRCloudTenant[]> [-IncludeBackups] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes cloud tenant accounts. You can remove the accounts of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

The tenant account is removed permanently from Veeam Backup & Replication. The service provider cannot undo this operation.

When you remove a cloud tenant account that was using WAN accelerators, the WAN accelerators' cache is cleared automatically.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenant | Specifies the array of tenant accounts you want to remove. | Accepts the [VBRCloudTenant[]](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| IncludeBackups | Defines that the cmdlet will remove all tenant backups. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing All Cloud Tenant Accounts

|  |  |
| --- | --- |
| This example shows how to remove all cloud tenant accounts registered in Veeam Backup & Replication.  |  | | --- | | $cloudtenants = Get-VBRCloudTenant  Remove-VBRCloudTenant -CloudTenant $cloudtenants |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Save the result to the $cloudtenants variable. 2. Run the Remove-VBRCloudTenant cmdlet. Set the $cloudtenants variable as the CloudTenant parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Cloud Director Tenant Account

|  |  |
| --- | --- |
| This example shows how to remove a Cloud Director tenant account.  |  | | --- | | $vCDtenant = Get-VBRCloudTenant -Name "vCD Tenant"  Remove-VBRCloudTenant -CloudTenant $vCDtenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet.  Specify the Name parameter value. Save the result to the $vCDtenant variable. 2. Run the Remove-VBRCloudTenant cmdlet. Set the $vCDtenant variable as the CloudTenant parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing All Cloud Tenant Accounts by Repository

|  |  |
| --- | --- |
| This example shows how to remove all cloud tenant accounts by specifying their backup repository.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Backups Vol2"  $tenant = Get-VBRCloudTenant -Repository $repository  Remove-VBRCloudTenant -CloudTenant $tenant |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Set the $repository variable as the Repository parameter value. Save the result to the $tenant variable. 3. Run the Remove-VBRCloudTenant cmdlet. Set the $tenant variable as the CloudTenant parameter value. |

Related Commands

* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
