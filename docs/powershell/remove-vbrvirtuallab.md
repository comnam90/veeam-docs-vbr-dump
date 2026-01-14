---
title: "Remove-VBRVirtualLab"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrvirtuallab.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRVirtualLab

In this article

Short Description

Removes virtual labs from Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRVirtualLab -VirtualLab <VBRVirtualLab[]> [-FromHost] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes virtual labs from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VirtualLab | Specifies a virtual lab. The cmdlet will remove this virtual lab from the Veeam Backup & Replication infrastructure. | Accepts the VBRVirtualLab[] object. To get this object, run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. | True | 0 | True (ByValue, |
| FromHost | Defines that the cmdlet will remove virtual lab from Veeam Backup & Replication and VMware infrastructure.  If you specify this parameter, the cmdlet will remove a virtual lab from both Veeam Backup & Replication and VMware infrastructures. Otherwise, the cmdlet will remove the virtual lab from the VMware infrastructure only. | SwitchParamter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParamter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Virtual Lab from Veeam Backup & Replication

|  |  |
| --- | --- |
| This example shows how to remove the Exchange 01 virtual lab from Veeam Backup & Replication.  |  | | --- | | $lab = Get-VBRVirtualLab -Name "Exchange 01"  Remove-VBRVirtualLab -VirtualLab $lab |  Perform the following steps:   1. Run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the Remove-VBRVirtualLab cmdlet. Set the $lab variable as the VirtualLab parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Virtual Lab from Veeam Backup & Replication![](//img.veeam.com/helpcenter/baggage/arrow_next.svg) and VMware Infrastructure

|  |  |
| --- | --- |
| This example shows how to remove the SQL07 virtual lab from Veeam Backup & Replication and the VMware infrastructure.  |  | | --- | | $lab = Get-VBRVirtualLab -Name "SQL07"  Remove-VBRVirtualLab -VirtualLab $lab -FromHost |  Perform the following steps:   1. Run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the Remove-VBRVirtualLab cmdlet. Set the $lab variable as the VirtualLab parameter value. Provide the FromHost parameter. |

Related Commands

[Get-VBRVirtualLab](get-vbrvirtuallab.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
