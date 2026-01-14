---
title: "Enable-VBRCloudTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRCloudTenant

In this article

Short Description

Enables disabled cloud tenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Enable-VBRCloudTenant -CloudTenant <IVBRTenant[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet enables selected cloud tenant accounts that were previously disabled. You can enable the cloud tenants accounts of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

Run the [Disable-VBRCloudTenant](disable-vbrcloudtenant.md) cmdlet to disable the tenant account.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenant | Specifies an array of cloud tenant accounts you want to enable. | Accepts the [VBRCloudTenant[]](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Cloud Director Tenant Account

|  |  |
| --- | --- |
| This example shows how to enable a Cloud Director tenant account.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "vCD Tenant"  Enable-VBRCloudTenant -CloudTenant $tenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter. Save the result to the $tenant variable. 2. Run the Enable-VBRCloudTenant cmdlet. Set the $tenant variable as the CloudTenant parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Several Cloud Tenant Accounts

|  |  |
| --- | --- |
| This example shows how to enable several cloud tenant accounts.  |  | | --- | | $cloudtenants = Get-VBRCloudTenant -Name "ABC Company Tenant", "vCD Tenant"  Enable-VBRCloudTenant -CloudTenant $cloudtenants |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter. Save the result to the $cloudtenants variable. 2. Run the Enable-VBRCloudTenant cmdlet. Set the $cloudtenants variable as the CloudTenant parameter value. |

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
