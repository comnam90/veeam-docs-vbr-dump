---
title: "Start-VBRFailoverPlan"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrfailoverplan.html"
last_updated: "12/23/2024"
product_version: "13.0.1.1071"
---

# Start-VBRFailoverPlan

In this article

Short Description

Starts failover by failover plan.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start failover by failover plan.

|  |
| --- |
| Start-VBRFailoverPlan -FailoverPlan <VBRFailoverPlan[]> [-Wait] [-Force] [<CommonParameters>] |

* Start failover to a specific restore point.

|  |
| --- |
| Start-VBRFailoverPlan -FailoverPlan <VBRFailoverPlan[]> [-FromDate <datetime>] [-Wait] [-Force] [<CommonParameters>] |

* Start failover in test mode.

|  |
| --- |
| Start-VBRFailoverPlan -FailoverPlan <VBRFailoverPlan[]> [-Wait] [-Force] [-KeepAliveDuration <Int32>] [-Test]  [<CommonParameters>] |

Detailed Description

This cmdlet starts failover by failover plan. With this cmdlet, you can start a number of failover processes.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FailoverPlan | Specifies the array of failover plans you want to start. | Accepts the [VBRFailoverPlan](vbrfailoverplan.md) or [VBRCloudFailoverPlan](vbrcloudfailoverplan.md) objects. To get these objects, run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. | True | Named | True (ByValue, |
| FromDate | Use this parameter to fail over to a particular restore point.  Specifies the date and time to which you want to fail over. Veeam Backup & Replication will find a restore point closest to this moment.  If omitted, Veeam Backup & Replication will fail over to the latest restore point. | DateTime | False | Named | False |
| Wait | Use this parameter to manage starting multiple failover processes.  If you provide this parameter, the next failover process will wait for the previous to end. | SwitchParameter | False | Named | False |
| Force | Used for cloud failovers to start full failover after the user's site is already partially failed over to cloud replicas.  If you provide this parameter, the cmdlet turns off the user appliance without notifying the user. Otherwise, the cmdlet will display a warning. | SwitchParameter | False | Named | False |
| KeepAliveDuration | Specifies a timeout in minutes for a CDP replicas failover test. The CDP replica will be active during this period of time.  Note: Consider the following:   * You must use the Test parameter. * To stop the failover testing beforehand, run the [Undo-VBRFailoverPlan](undo-vbrfailoverplan.md). | Int32 | False | Named | False |
| Test | Defines that the failover runs in test mode. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupSession](vbrbackupsession.md)[]

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Failover Plan [Using Pipeline]

|  |  |
| --- | --- |
| This command starts failover process by the MS Exchange Group Failover failover plan. The VMs in the failover group are failed over to the latest restore point.  |  | | --- | | Get-VBRFailoverPlan -Name "MS Exchange Group Failover" | Start-VBRFailoverPlan |  Perform the following steps:   1. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Start-VBRFailoverPlan cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Failover Plan [Using Variable]

|  |  |
| --- | --- |
| This example shows how to start failover process by the MS Exchange Group Failover failover plan. The VMs in the failover group are failed over to the latest restore point.  |  | | --- | | $MSExchangeGroup = Get-VBRFailoverPlan -Name "MS Exchange Group Failover"  Start-VBRFailoverPlan -FailoverPlan $MSExchangeGroup |  Perform the following steps:   1. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. Save the result to the $MSExchangeGroup variable. 2. Run the Start-VBRFailoverPlan cmdlet. Set the $MSExchangeGroup variable as the FailoverPlan parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Failover Plans for Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to start failover processes by the MS Exchange Group Failover and SQLServers Group Failover failover plans. The VMs are failed over to a week ago state. The VM groups are failed over one by one.  |  | | --- | | $date = Get-Date  Get-VBRFailoverPlan -Name "MS Exchange Group Failover", "SQLServers Group Failover" | Start-VBRFailoverPlan -FromDate $date.AddDays(-7) -Wait |  Perform the following steps:   1. The date is obtained with the Get-Date command. Save it to the $date variable. 2. Run the [Get-VBRFailoverPlan](get-vbrfailoverplan.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Start-VBRFailoverPlan cmdlet. Set the $date variable as the FromDate parameter value. Provide the Wait parameter. |

Related Commands

* [Get-VBRFailoverPlan](get-vbrfailoverplan.md)
* [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)

Page updated 12/23/2024

Page content applies to build 13.0.1.1071
