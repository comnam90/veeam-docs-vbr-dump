---
title: "Reset-VBRCloudTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbrcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Reset-VBRCloudTenant


Short Description

Resets licenses for cloud account tenants.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Reset-VBRCloudTenant -CloudTenant <IVBRTenant[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet resets cloud account tenant license. You can reset the license for the cloud tenant accounts of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenant | Specifies the array of tenant accounts for which you want to reset the tenant license. | Accepts the [VBRCloudTenant[]](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Resetting License for Simple Cloud Tenant

|  |  |
| --- | --- |
| This example shows how to reset a license for the simple cloud tenant.  |  | | --- | | $simpletenant = Get-VBRCloudTenant -Name "ABC Company"  Reset-VBRCloudTenant -CloudTenant $simpletenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $simpletenant variable. 2. Run the Reset-VBRCloudTenant cmdlet. Set the $simpletenant variable as the CloudTenant parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Resetting License for Cloud Director Tenant

|  |  |
| --- | --- |
| This example shows how to reset a license for the Cloud Director tenant account.  |  | | --- | | $CloudUsers = Get-VBRCloudTenant -Name "CloudUser\*"  Reset-VBRCloudTenant -CloudTenant $CloudUsers |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $CloudUsers variable. 2. Run the Reset-VBRCloudTenant cmdlet. Set the $CloudUsers variable as the CloudTenant parameter value. |

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)


