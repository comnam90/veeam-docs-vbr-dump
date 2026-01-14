---
title: "Enable-VBRCloudSubTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcloudsubtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRCloudSubTenant

In this article

Short Description

Enables disabled cloud subtenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRCloudSubTenant -SubTenant <IVBRCloudSubTenant[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet enables selected cloud subtenant accounts that were previously disabled. You can enable the following types of cloud subtenant accounts:

* Simple cloud subtenant accounts
* Cloud Director subtenant accounts

Run the [Disable-VBRCloudSubTenant](disable-vbrcloudsubtenant.md) cmdlet to disable the subtenant account.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SubTenant | Specifies the array of cloud subtenants that you want to enable. The subtenants can have different parents. | Accepts the IVBRCloudSubTenant[] object. To get this object, run the [Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling Cloud Subtenant

This example shows how to enable a cloud subtenant.

|  |
| --- |
| $subtenant = Get-VBRCloudSubTenant -Name "Alpha"  Enable-VBRCloudSubTenant -SubTenant $subtenant |

Perform the following steps:

1. Run the [Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $subtenant variable.
2. Run the Enable-VBRCloudSubTenant cmdlet. Set the $subtenant variable as the SubTenant parameter value.

Related Commands

[Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
