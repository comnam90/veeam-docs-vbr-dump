---
title: "Set-VBRFailoverPlanObject"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrfailoverplanobject.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Set-VBRFailoverPlanObject

In this article

Short Description

Modifies VMs in failover plans.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRFailoverPlanObject -Object <VBRFailoverPlanObject> [-BootOrder <int>] [-BootDelay <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies VMs added to a failover plan.

Run the [Set-VBRCloudFailoverPlanObject](set-vbrcloudfailoverplanobject.md) cmdlet to modify VMs in cloud failover plans.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Object | Specifies the VM you want modify. | Accepts the [VBRFailoverPlanObject](vbrfailoverplanobject.md) object. To get this object, run the [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) cmdlet. | True | Named | True (ByValue, |
| BootOrder | Specifies the new value for the order number by which the VM will boot. | Int32 | False | Named | False |
| BootDelay | Specifies the new value for the delay time for the VM.  The delay time is set in seconds.  Default: 60 sec.  If you set boot delay to 0 to a number of VMs, these VMs will start simultaneously. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRFailoverPlanObject](vbrfailoverplanobject.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting New Boot Delay Value [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set a new boot delay value for the server that was earlier assigned to the $MSExchange01 variable.  |  | | --- | | $MSExchange01 = Find-VBRViEntity -Name "MSExchange01" | New-VBRFailoverPlanObject -BootDelay 0  $MSExchange01 | Set-VBRFailoverPlanObject -BootDelay 120 |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) cmdlet. Specify the BootDelay parameter value. Save the result to the $MSExchange01 variable to be used with other cmdlets. 2. Pipe the $MSExchange01 variable output to the Set-VBRFailoverPlanObject cmdlet. Specify the BootDelay parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting New Boot Delay Value [Using Variable]

|  |  |
| --- | --- |
| This example shows how to set a new boot delay value for the server that was earlier assigned to the $MSExchange01 variable.  |  | | --- | | $MSExchange01 = Find-VBRViEntity -Name "MSExchange01" | New-VBRFailoverPlanObject -BootDelay 0  $MSExchange01 = Set-VBRFailoverPlanObject -Object $MSExchange01 -BootDelay 120 |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the [New-VBRFailoverPlanObject](new-vbrfailoverplanobject.md) cmdlet. Specify the BootDelay parameter value. Save the result to the $MSExchange01 variable to be used with other cmdlets. 2. Run the Set-VBRFailoverPlanObject cmdlet. Set the $MSExchange01 variable as the Object parameter value. Specify the BootDelay parameter values. Save the result to the $MSExchange01 variable to be used with other cmdlets. |

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
