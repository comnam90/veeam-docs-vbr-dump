---
title: "Disable-VBRCloudTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRCloudTenant


Short Description

Disables cloud tenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Disable-VBRCloudTenant -CloudTenant <IVBRTenant[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables a cloud tenant account. When you disable a tenant account, the tenant cannot use their account resources. You can disable the cloud tenant accounts of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

Run the [Enable-VBRCloudTenant](enable-vbrcloudtenant.md) cmdlet to enable a disabled account.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenant | Specifies the array of cloud tenant accounts you want to disable. | Accepts the [VBRCloudTenant[]](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Cloud Tenant Account

|  |  |
| --- | --- |
| This example shows how to disable a Cloud Director tenant account.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "vCD Tenant"  Disable-VBRCloudTenant -CloudTenant $tenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter. Save the result to the $tenant variable. 2. Run the Disable-VBRCloudTenant cmdlet. Set the $tenant variable as the CloudTenant parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Several Cloud Tenant Accounts

|  |  |
| --- | --- |
| This example shows how to disable several cloud tenant accounts.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company Tenant", "vCD Tenant"  Disable-VBRCloudTenant -CloudTenant $tenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the Disable-VBRCloudTenant cmdlet. Set the $tenant variable as the CloudTenant parameter value. |

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)


