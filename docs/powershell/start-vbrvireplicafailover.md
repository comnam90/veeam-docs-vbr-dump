---
title: "Start-VBRViReplicaFailover"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvireplicafailover.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Start-VBRViReplicaFailover


Short Description

Fails over corrupted VMware VMs to their replicas.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Perform failover.

|  |
| --- |
| Start-VBRViReplicaFailover -RestorePoint <COib> [-Reason <string>] [-RunAsync] [-PowerOn] [-ReIp] [-WhatIf] [-Confirm]   [<CommonParameters>] |

* Perform permanent failover.

|  |
| --- |
| Start-VBRViReplicaFailover -RestorePoint <COib> [-Reason <string>] [-RunAsync] [-Definite] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Perform planned failover.

|  |
| --- |
| Start-VBRViReplicaFailover -RestorePoint <COib> [-Reason <string>] [-RunAsync] [-Planned] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet fails over a corrupted VMware VM to its successfully created replica.

Run the [Start-VBRViReplicaFailback](start-vbrvireplicafailback.md) cmdlet to fail back to the original VM.

Run the [Stop-VBRReplicaFailover](stop-vbrreplicafailover.md) cmdlet to undo failover.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the replica restore point to which you want to fail over. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, |
| Reason | Specifies the reason for performing a failover. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| PowerOn | Defines that the cmdlet will power on replica VM after the failover. Otherwise, you will need to power on the replica VM manually. | SwitchParameter | False | Named | False |
| ReIp | Defines that the replica will use the re-IP rules that are set in the replication job.  Note: Do not enable the re-IP if the re-IP rules are not configured in the replication job. | SwitchParameter | False | Named | False |
| Definite | Defines that the failover is permanent. | SwitchParameter | False | Named | False |
| Planned | Defines that the failover is planned.  Default: The planned failover option is enabled. | SwitchParameter | False | Named | False |
| WhatIf | Specifies whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Failover to VM Replica

|  |  |
| --- | --- |
| This example shows how to perform failover to the WebServer VM replica.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer"  Start-VBRViReplicaFailover -RestorePoint $restorepoint[3] -Reason "Data recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Start-VBRViReplicaFailover cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point is used.   * Specify the Reason parameter value. * Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failover to Latest Restore Point [Using Pipeline]

|  |  |
| --- | --- |
| This command fails over to the latest restore point of the WebServer VM replica.  |  | | --- | | Get-VBRRestorePoint -Name "WebServer" | Sort-Object $\_.creationtime -Descending | Select-Object -First 1 | Start-VBRViReplicaFailover -Reason "Configuration recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the .creationtime property for the $\_ variable. Provide the Descending parameter. 3. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Utility/Select-Object?view=powershell-7) cmdlet. Set the 1 number as the First parameter value. 4. Pipe the cmdlet output to the Start-VBRViReplicaFailover cmdlet. Specify the Reason parameter value. Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Planned Failover to VM Replica

|  |  |
| --- | --- |
| This example shows how to perform planned failover of the WebServer VM.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer"  Start-VBRViReplicaFailover -RestorePoint $restorepoint[3] -Reason "Tsunami forecast" -Planned |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable.  1. Run the Start-VBRViReplicaFailover cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point is used.   * Specify the Reason parameter value. * Provide the Planned parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Performing Permanent Failover

|  |  |
| --- | --- |
| This example shows how to perform permanent failover of the WebServer VM.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer"  Start-VBRViReplicaFailover -RestorePoint $restorepoint[3] -Reason "Configuration recovery" -RunAsync -Definite |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable.  1. Run the Start-VBRViReplicaFailover cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point is used.   * Specify the Reason parameter value.  * Provide the RunAsync parameter.  * Provide the Definite parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7)
* [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7)


