---
title: "Remove-VBRCloudHardwarePlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudhardwareplan.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudHardwarePlan


Short Description

Removes hardware plans.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Remove-VBRCloudHardwarePlan -HardwarePlan <VBRCloudHardwarePlan[]> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected hardware plan.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| HardwarePlan | Specifies the array of hardware plans you want to remove. | Accepts [VBRViCloudHardwarePlan[]](vbrvicloudhardwareplan.md) or [VBRHvCloudHardwarePlan[]](vbrhvcloudhardwareplan.md) object. To get this object, run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. | True | Named | True (ByValue, |
| Force | Defines that the cmdlet remove the hardware plan without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Hardware Plans [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove VMware Silver and VMware Gold hardware plans.  |  | | --- | | $hardwareplans = Get-VBRCloudHardwarePlan -Name "VMware Silver", "VMware Gold"  Remove-VBRCloudHardwarePlan -HardwarePlan $hardwareplans |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. Save the result to the $hardwareplans variable. 2. Run the Remove-VBRCloudHardwarePlan cmdlet. Set the $hardwareplans variable as the HardwarePlan parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Hardware Plan [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove a hardware plan named Hyper-V Silver.  |  | | --- | | Get-VBRCloudHardwarePlan -Name "Hyper-V Silver" | Remove-VBRCloudHardwarePlan |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRCloudHardwarePlan cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing VMware Hardware Plans [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove all VMware hardware plans.  |  | | --- | | Get-VBRCloudHardwarePlan -Platform VMware | Remove-VBRCloudHardwarePlan |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Set the VMware option for the Platform parameter. 2. Pipe the cmdlet output to the Remove-VBRCloudHardwarePlan cmdlet. |

Related Commands

[Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md)


