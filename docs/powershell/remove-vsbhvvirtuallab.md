---
title: "Remove-VSBHvVirtualLab"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vsbhvvirtuallab.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VSBHvVirtualLab

In this article

Short Description

Removes a Hyper-V virtual lab.

|  |
| --- |
| ![Remove-VSBHvVirtualLab](images/icon_note.webp) Note: |
| This cmdlet is deprecated and will be marked as obsolete in the future. It is recommended to re-write your scripts using the cmdlet. |

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VSBHvVirtualLab -VirtualLab <CHvSbVirtualLab[]> [-FromHost] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Hyper-V virtual labs.

You can remove virtual labs from the Veeam Backup & Replication console or from Hyper-V hosts. To remove virtual labs from Hyper-V hosts, use the FromHost parameter.

If you remove a virtual lab from the Veeam Backup & Replication console, you can add it back by running the [Connect-VSBHvVirtualLab](connect-vsbhvvirtuallab.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| VirtualLab | Specifies the array of virtual lab names. The cmdlet will remove these virtual labs. | Accepts the CHvSbVirtualLab[] object. To get this object, run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. | True | Named | True(ByValue, ByProperty Name) |
| FromHost | Defines that the cmdlet will remove virtual labs from Hyper-V hosts. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Virtual Lab from Console

|  |  |
| --- | --- |
| This example shows how to remove a virtual lab from the Veeam Backup & Replication console.  |  | | --- | | $vlab = Get-VSBHvVirtualLab -Name "Virtual Lab 01"  Remove-VSBHvVirtualLab -VirtualLab $vlab |  Perform the following steps:   1. Run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $vlab variable. 2. Run the Remove-VSBHvVirtualLab cmdlet. Set the $vlab variable as the VirtualLab parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Virtual Lab from Hyper-V Host

|  |  |
| --- | --- |
| This example shows how to remove a virtual lab from the Hyper-V host.  |  | | --- | | $vlab = Get-VSBHvVirtualLab -Name "Virtual Lab 01"  Remove-VSBHvVirtualLab -VirtualLab $vlab -FromHost |  Perform the following steps:   1. Run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $vlab variable. 2. Run the Remove-VSBHvVirtualLab cmdlet. Set the $vlab variable as the VirtualLab parameter value. Provide the FromHost parameter. |

Related Commands

[Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
