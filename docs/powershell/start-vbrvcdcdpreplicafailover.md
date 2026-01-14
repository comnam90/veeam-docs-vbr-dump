---
title: "Start-VBRvCDCDPReplicaFailover"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcdcdpreplicafailover.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Start-VBRvCDCDPReplicaFailover

In this article

Short Description

Starts to perform failover to a Cloud Director CDP replica.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start to perform failover to a restore point created at a specific date and time.

|  |
| --- |
| Start-VBRvCDCDPReplicaFailover -Replica <VBRvCDCDPReplica> [-ToPointInTime <datetime>] [-Reason <string>] [-Commit] [-Retry] [-PowerOn] [-Force] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Start to perform failover to a specific long-term restore point of a Cloud Director CDP replica.

|  |
| --- |
| Start-VBRvCDCDPReplicaFailover -Replica <VBRvCDCDPReplica> -LongTermRestorePoint <VBRvCDCDPLongTermRestorePoint> [-Reason <string>] [-Commit] [-Retry] [-PowerOn] [-Force] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet starts to perform failover to a Cloud Director CDP replica. The replica must be in the Ready state.

|  |
| --- |
| Important |
| Before you start to perform failover to Cloud Director CDP replicas we recommend to the run the [Get-VBRvCDCDPShortTermRestoreInterval](get-vbrvcdcdpshorttermrestoreinterval.md) cmdlet to get a list of all replicated states that are available for replicas. This allows you to verify that you do not perform failover to replicated states of replicas that do not exist. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies the replica to which you want to fail over. | Accepts the VBRvCDCDPReplica object. To get this object, run the [Get-VBRCDPReplica](get-vbrcdpreplicavcd.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| LongTermRestorePoint | Specifies a long-term restore point of a replica. The cmdlet will perform failover to this restore point. | Accepts the VBRvCDCDPLongTermRestorePoint object. To get this object, run the [Get-VBRvCDCDPLongTermRestorePoint](get-vbrvcdcdplongtermrestorepoint.md) cmdlet. | True | Named | False |
| ToPointInTime | Specifies date and time when a restore point was created. The cmdlet will perform failover to the restore point created at the specified date and time. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | False | Named | False |
| Reason | Specifies the reason for performing failover. | String | False | Named | False |
| Commit | Defines whether the cmdlet will perform permanent failover.  If you provide this parameter, the cmdlet will switch from the original vApp to the replica and will set for the replica the role of the original vApp.  If you do not provide this parameter, the cmdlet will not set for the replica the role of the original vApp after performing a failover. | SwitchParameter | False | Named | False |
| Retry | Defines that if failover does not complete successfully, the cmdlet will start to perform failover again.  If you do not specify this parameter, the cmdlet will not start to perform failover if any vApps are in the incomplete state. | SwitchParameter | False | Named | False |
| PowerOn | Defines that the cmdlet will power on the replica after performing failover. If you do not want to power on the replica, set the parameter to $false.  Default: True.  Note: If you provide this parameter with the Commit parameter, the cmdlet will always start the replica. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform failover without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

SessionId <Guid>

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Failover to Restore Point Created at Specific Sate and Time

|  |  |
| --- | --- |
| This example shows how to perform failover to a restore point created at a specific date and time.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win07"  $date = Get-Date  -Year 2020 -Month 2 -Day 2 -Hour 0 -Minute 0 -Second 0  Start-VBRvCDCDPReplicaFailover -Replica $replica -ToPointInTime $date |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $date variable. 3. Run the Start-VBRvCDCDPReplicaFailover cmdlet. Set the $replica variable as the Replica parameter value. Set the $date variable as the ToPointInTime parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failover to Specific Long-Term Restore Point Created of Cloud Director CDP Replica

|  |  |
| --- | --- |
| This example shows how to perform failover to a specific long-term restore point of a Cloud Director CDP replica.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win07"  $restorepoint = Get-VBRvCDCDPLongTermRestorePoint -Replica $replica  Start-VBRvCDCDPReplicaFailover -Replica $replica -LongTermRestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet.  Specify the Name parameter value. Save the result to the $replica variable. 2. Run the [Get-VBRvCDCDPLongTermRestorePoint](get-vbrvcdcdplongtermrestorepoint.md) cmdlet. Set the $replica variable as the Replica parameter value. Save the result to the $restorepoint variable. 3. Run the Start-VBRvCDCDPReplicaFailover cmdlet. Set the $replica variable as the Replica parameter value. Set the $restorepoint variable as the LongTermRestorePoint parameter value. |

Related Commands

* [Get-VBRCDPReplica](get-vbrcdpreplica.md)
* [Get-Date](get-hp3infrastructurevolume.md)
* [Get-VBRvCDCDPLongTermRestorePoint](get-vbrvcdcdplongtermrestorepoint.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
