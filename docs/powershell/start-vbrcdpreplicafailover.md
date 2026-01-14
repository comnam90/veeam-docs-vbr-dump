---
title: "Start-VBRCDPReplicaFailover"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcdpreplicafailover.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Start-VBRCDPReplicaFailover

In this article

Short Description

Starts to perform failover to VM replicas.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start to perform failover to a specific restore point of VM replicas.

|  |
| --- |
| Start-VBRCDPReplicaFailover -Replica <VBRCDPReplica> [-ToPointInTime <datetime>] [-Reason <string>] [-Commit] [-PowerOn] [-Force] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Start to perform failover to a specific long-term restore point of VM replicas.

|  |
| --- |
| Start-VBRCDPReplicaFailover -Replica <VBRCDPReplica> -LongTermRestorePoint <VBRCDPLongTermRestorePoint> [-Reason <string>] [-Commit] [-PowerOn] [-Force] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Start to perform planned failover.

|  |
| --- |
| Start-VBRCDPReplicaFailover -Replica <VBRCDPReplica> [-Planned] [-Reason <String>] [-Commit] [-PowerOn] [-Force] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet starts to perform failover to VM replicas.

|  |
| --- |
| Important |
| Before you start to perform failover to VM replicas we recommend to the run the [Get-VBRCDPShortTermRestoreInterval](get-vbrcdpshorttermrestoreinterval.md) cmdlet to get a list of all replicated states that are available for VM replicas. This allows you to verify that you will not perform failover to replicated states of VM replicas that do not exist. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies a VM protected with CDP to which you want to perform failover. | Accepts the VBRCDPReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ToPointInTime | Specifies a replicated state that is available for a VM protected with CDP. | DateTime | False | Named | False |
| LongTermRestorePoint | Specifies a long-term restore point of a VM protected with CDP. The cmdlet will perform failover to this restore point. | Accepts the VBRCDPLongTermRestorePoint object. To get this object, run the [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md) cmdlet. | False | Named | False |
| Planned | Defines that the cmdlet will perform planned failover. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing failover. | String | False | Named | False |
| Commit | Defines that the cmdlet will perform permanent failover of the specified replicas in the failover state.   * If you provide this parameter, the cmdlet will permanently switch processes from the original VM to the VM protected with CDP and will set for the CDP replica a role of the original VM. * If you do not provide this parameter, the cmdlet will not set the CDP replica a role of the original VM after performing a failover. | SwitchParameter | False | Named | False |
| PowerOn | Defines that the cmdlet will power on a CDP replica after performing failover. If you do not provide this parameter, the cmdlet will power on the replica. If you do not want to power on the replica, set the parameter to the PowerOn:$false value.  Default: True.  Note: If you provide this parameter with the Commit parameter, the cmdlet will always start a replica. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform a failover without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Failover to CDP Replica Latest Restore Point

|  |  |
| --- | --- |
| This example show how to perform a failover to the latest restore point. The cmdlet will perform a failover without without showing warnings in the PowerShell console.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win05"  Start-VBRCDPReplicaFailover -Replica $replica -Force |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Start-VBRCDPReplicaFailover cmdlet. Set the $replica variable as the Replica parameter. Provide the Force parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failover to CDP Replica Replicated State

|  |  |
| --- | --- |
| This example shows to perform a failover to a specific replicated state of the CDP replica of the Win05 VM.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win05"  $restorepoints = Get-VBRCDPShortTermRestoreInterval -Replica $replica  $date = Get-Date -Year 2020 -Month 2 -Day 2 -Hour 0 -Minute 0 -Second 0  Start-VBRCDPReplicaFailover -Replica $replica -ToPointInTime $date |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the [Get-VBRCDPShortTermRestoreInterval](get-vbrcdpshorttermrestoreinterval.md) cmdlet. Specify the Replica parameter value. Check a list of all replicated states that are available for VM replicas. 3. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $date variable. 4. Run the Start-VBRCDPReplicaFailover cmdlet. Set the $replica variable as the Replica parameter. Set the $date variable as the ToPointInTime parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Failover to CDP Replica Long-Term Restore Point

|  |  |
| --- | --- |
| This example shows how to start to perform a failover to a specific long-term restore point of the CDP replica of the Win05 VM.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win05"  $restorepoint = Get-VBRCDPLongTermRestorePoint -Replica $replica -ApplicationConsistent  Start-VBRCDPReplicaFailover -Replica $replica -LongTermRestorePoint $restorepoint[0] -Force |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md) cmdlet. Specify the Replica and ApplicationConsistent parameter values. Save the result to the $restorepoint variable. 3. Run the Start-VBRCDPReplicaFailover cmdlet. Specify the following settings:  * Set the $replica variable as the Replica parameter. * Set the $restorepoint[0] variable as the LongTermRestorePoint parameter. * Provide the Force parameter. |

Related Commands

* [Get-VBRCDPReplica](get-vbrcdpreplica.md)
* [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md)
* [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
