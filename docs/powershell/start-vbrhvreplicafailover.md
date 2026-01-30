---
title: "Start-VBRHvReplicaFailover"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrhvreplicafailover.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Start-VBRHvReplicaFailover


Short Description

Fails over corrupted Hyper-V VMs to their replicas.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Perform failover.

|  |
| --- |
| Start-VBRHvReplicaFailover -RestorePoint <COib> [-Reason <string>] [-RunAsync]  [<CommonParameters>] |

* Perform permanent failover.

|  |
| --- |
| Start-VBRHvReplicaFailover -RestorePoint <COib> [-Reason <string>] [-RunAsync] [-Definite]  [<CommonParameters>] |

* Perform planned failover.

|  |
| --- |
| Start-VBRHvReplicaFailover -RestorePoint <COib> [-Reason <string>] [-RunAsync] [-Planned]  [<CommonParameters>] |

Detailed Description

This cmdlet fails over a corrupted Hyper-V VM to its successfully created replica.

This cmdlet provides 3 parameter sets for the following operations:

* Failover
* Permanent failover
* Planned failover

Run the [Start-VBRHvReplicaFailback](start-vbrhvreplicafailback.md) cmdlet to fail back to the original VM.

Run the [Stop-VBRReplicaFailover](stop-vbrreplicafailover.md) cmdlet to undo failover. You can also undo planned failover.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the replica restore point to which you want to fail over. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, |
| Reason | Specifies the reason for performing a failover. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Definite | Defines that the failover is permanent. | SwitchParameter | False | Named | False |
| Planned | Defines that the failover is planned. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Planned Failover to VM Replica

|  |  |
| --- | --- |
| This example shows how to perform failover to the Hyper-V WebServer VM replica.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "Hyper-V WebServer"  Start-VBRHvReplicaFailover -RestorePoint $restorepoint[1] -Reason "Data recovery" -RunAsync -Planned |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Start-VBRHvReplicaFailover cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the second restore point is used.   * Specify the Reason parameter value. * Provide the RunAsync parameter. * Provide the Planned parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Permanent Failover to VM Replica

|  |  |
| --- | --- |
| This example shows how to perform failover to the Hyper-V WebServer VM replica.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "Hyper-V WebServer"  Start-VBRHvReplicaFailover -RestorePoint $restorepoint[3] -Reason "Data recovery" -RunAsync -Definite |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Start-VBRHvReplicaFailover cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point is used.   * Specify the Reason parameter value. * Provide the RunAsync parameter. * Provide the Definite parameter. |

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)


