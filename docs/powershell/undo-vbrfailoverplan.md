---
title: "Undo-VBRFailoverPlan"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/undo-vbrfailoverplan.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Undo-VBRFailoverPlan

In this article

Short Description

Undoes the failover by failover plan.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Undo-VBRFailoverPlan -FailoverPlan <VBRFailoverPlan[]> [-Wait] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet undoes the failover process. Undoing failover switches the workload back to source VMs. All changes that were made to the replicas during failover are discarded.

To switch back to the production VM and synchronize the changes made to the replica while failover, start failback process. Run the [Start-VBRViReplicaFailback](start-vbrvireplicafailback.md) or the [Start-VBRHvReplicaFailback](start-vbrhvreplicafailback.md) cmdlet to fail back to the VMware or Hyper-V production VM. Note that failback is not a group process and must be performed for each VM individually.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FailoverPlan | Specifies the array of failover plans you want to undo. | Accepts the [VBRFailoverPlan](vbrfailoverplan.md) or [VBRCloudFailoverPlan](vbrcloudfailoverplan.md) objects. To get these objects, run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. | True | Named | True (ByValue, |
| Wait | Use this parameter to manage undoing multiple failover processes.  If you provide this parameter, the next undo failover process will wait for the previous to end. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupSession](vbrbackupsession.md)[]

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Undoing Failover Plan [Using Pipeline]

|  |  |
| --- | --- |
| This command undoes the failover process by the MS Exchange Group Failover failover plan.  |  | | --- | | Get-VBRFailoverPlan -Name "MS Exchange Group Failover" | Undo-VBRFailoverPlan |  Perform the following steps:   1. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Undo-VBRFailoverPlan cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Undoing Failover Plan [Using Variable]

|  |  |
| --- | --- |
| This command undoes the failover process by the MS Exchange Group Failover failover plan.  |  | | --- | | $MSExchangeGroup = Get-VBRFailoverPlan -Name "MS Exchange Group Failover"  Undo-VBRFailoverPlan -FailoverPlan $MSExchangeGroup |  Perform the following steps:   1. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. Save the result to the $MSExchangeGroup variable. 2. Run the Undo-VBRFailoverPlan cmdlet. Set the $MSExchangeGroup variable as the FailoverPlan parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Undoing Failover Plans [Using Pipeline]

|  |  |
| --- | --- |
| This command undoes failover processes by the MS Exchange Group Failover and SQLServers Group Failover failover plans. The VM groups are processed one by one.  |  | | --- | | Get-VBRFailoverPlan -Name "MS Exchange Group Failover", "SQLServers Group Failover" | Undo-VBRFailoverPlan -Wait |  Perform the following steps:   1. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Undo-VBRFailoverPlan cmdlet. Provide the Wait parameter. |

Related Commands

[Get-VBRFailoverPlan](get-vbrfailoverplan.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
