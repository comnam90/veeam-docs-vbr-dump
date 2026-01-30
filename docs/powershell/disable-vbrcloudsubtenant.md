---
title: "Disable-VBRCloudSubTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcloudsubtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRCloudSubTenant


Short Description

Disables cloud subtenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRCloudSubTenant -SubTenant <IVBRCloudSubTenant[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables a cloud subtenant account. When you disable a subtenant account, the subtenant cannot use their account resources. You can disable cloud subtenant accounts of the following types:

* Simple cloud subtenant accounts
* Cloud Director subtenant accounts

Run the [Enable-VBRCloudSubTenant](enable-vbrcloudsubtenant.md) cmdlet to enable a disabled account.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SubTenant | Specifies the array of cloud subtenants that you want to disable. The subtenants can have different parents. | Accepts the IVBRCloudSubTenant[] object. To get this object, run the [Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Cloud Subtenant

This example shows how to disable a cloud subtenant.

|  |
| --- |
| $subtenant = Get-VBRCloudSubTenant -Name "Alpha"  Disable-VBRCloudSubTenant -SubTenant $subtenant |

Perform the following steps:

1. Run the [Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $subtenant variable.
2. Run the Disable-VBRCloudSubTenant cmdlet. Set the $subtenant variable as the SubTenant parameter value.

Related Commands

[Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md)


