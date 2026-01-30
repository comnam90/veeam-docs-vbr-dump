---
title: "Remove-VBRFailoverPlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrfailoverplan.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRFailoverPlan


Short Description

Removes a selected failover plan or a cloud failover plan.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRFailoverPlan -FailoverPlan <VBRFailoverPlan[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected failover plan from Veeam Backup & Replication console and database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FailoverPlan | Specifies the array of failover plans you want to remove. | Accepts the [VBRFailoverPlan](vbrfailoverplan.md) or [VBRCloudFailoverPlan](vbrcloudfailoverplan.md) objects. To get these objects, run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Failover Plan [Using Pipeline]

|  |  |
| --- | --- |
| This command removes the MS Exchange Group Failover failover plan.  |  | | --- | | Get-VBRFailoverPlan -Name "MS Exchange Group Failover" | Remove-VBRFailoverPlan |  Perform the following steps:   1. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRFailoverPlan cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Failover Plan [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the MS Exchange Group Failover failover plan.  |  | | --- | | $MSExchangeGroup = Get-VBRFailoverPlan -Name "MS Exchange Group Failover"  Remove-VBRFailoverPlan -FailoverPlan $MSExchangeGroup |  Perform the following steps:   1. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. Save the result to the $MSExchangeGroup variable. 2. Run the Remove-VBRFailoverPlan cmdlet. Set the $MSExchangeGroup variable as the FailoverPlan parameter value. |

Related Commands

[Get-VBRFailoverPlan](get-vbrfailoverplan.md)


