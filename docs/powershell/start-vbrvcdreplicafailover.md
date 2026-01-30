---
title: "Start-VBRvCDReplicaFailover"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcdreplicafailover.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Start-VBRvCDReplicaFailover


Short Description

Starts to perform failover to a Cloud Director replica.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start to perform failover to a Cloud Director replica. In this scenario, if failover does not complete successfully, Veeam Backup & Replication will start to perform failover to a CDP replica again.

|  |
| --- |
| Start-VBRvCDReplicaFailover -RestorePoint <COib> [-Retry] [-Reason <string>] [-PowerOn] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Start to perform permanent failover to a Cloud Director replica.

|  |
| --- |
| Start-VBRvCDReplicaFailover -RestorePoint <COib> [-Definitive] [-Retry] [-Reason <string>] [-PowerOn] [-RunAsync][-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet starts to perform failover to a Cloud Director replica.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of a Cloud Director replica to which you want to perform failover. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Definitive | Defines that the cmdlet will perform a permanent failover of a Cloud Director replica.  If you do not specify this parameter, the cmdlet will not switch permanently from the original vApp to a Cloud Director replica.  Note: Before you perform permanent failover, make sure that your Cloud Director replica is in the Failover state. | SwitchParameter | False | Named | False |
| Retry | Defines that if failover does not complete successfully, Veeam Backup & Replication will start to perform failover to a Cloud Director replica again.  If you do not specify this parameter, the cmdlet will not start to perform failover to a Cloud Director replica if some VMs are in the incomplete state. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing failover. | String | False | Named | False |
| PowerOn | If set, the replica vApp will be powered on after the failback. Otherwise, you will need to power the vApp on manually. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform failover without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Failover to Cloud Director Replica

|  |  |
| --- | --- |
| This example shows how to perform failover to the WebServer Cloud Director replica.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer"  Start-VBRvCDReplicaFailover -RestorePoint $restorepoint[3] -Reason "Data recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Provide the vApp name as the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCDReplicaFailover cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).   * Specify the Reason parameter value. * Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failover to Cloud Director Replica with Retry Option

|  |  |
| --- | --- |
| This example shows how to perform failover to the WebServer Cloud Director replica. If failover does not complete successfully, Veeam Backup & Replication will start to perform failover to a Cloud Director replica again.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer"  Start-VBRvCDReplicaFailover -RestorePoint $restorepoint[3] -Retry -Reason "Data recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Provide the vApp name as the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCDReplicaFailover cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).   * Provide the Retry parameter. * Specify the Reason parameter value. * Provide the RunAsync parameter. |

|  |
| --- |
| Important |
| Before you perform permanent failover, make sure that your Cloud Director replica is in the Failover state. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Permanent Failover to Cloud Director Replica

|  |  |
| --- | --- |
| This example shows how to perform a permanent failover to the WebServer Cloud Director replica.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer"  Start-VBRvCDReplicaFailover -RestorePoint $restorepoint[3] -Definitive -Reason "Data recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Provide the vApp name as the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCDReplicaFailover cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).   * Provide the Definitive parameter. * Specify the Reason parameter value. * Provide the RunAsync parameter. |

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)


