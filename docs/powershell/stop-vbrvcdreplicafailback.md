---
title: "Stop-VBRvCDReplicaFailback"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrvcdreplicafailback.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRvCDReplicaFailback

In this article

Short Description

Stops a Cloud Director replica failback.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRvCDReplicaFailback -RestorePoint <COib> [-Force] [-PowerOn] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet stops a Cloud Director replica failback.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the Cloud Director replica. The cmdlet will stop failback of this replica. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| PowerOn | Defines that the cmdlet will power on replica VM after the failover. Otherwise, you will need to power on the replica VM manually. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform failover without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Undoing Failover

This example shows how to undo failback to the the WebServer Cloud Director replica.

|  |
| --- |
| $restorepoint = Get-VBRRestorePoint -Name "WebServer"  Stop-VBRvCDReplicaFailback -RestorePoint $restorepoint[3] -RunAsync |

Perform the following steps:

1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).

1. Run the Stop-VBRvCDReplicaFailover cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Provide the RunAsync parameter.

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
