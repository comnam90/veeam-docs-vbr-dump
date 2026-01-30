---
title: "Start-VBRReplicaFailover (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrreplicafailover.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Start-VBRReplicaFailover (obsolete)


Short Description

Fails over a corrupted VM to its replica.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to rewrite your scripts using the [Start-VBRViReplicaFailover](start-vbrvireplicafailover.md) cmdlet. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Start-VBRReplicaFailover -RestorePoint <COib> [-Reason <String>] [-Planned] [-RunAsync] [-WarningAction <ActionPreference>] [-WarningVariable <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you fail over a corrupted VM to its successfully created replica.

Performing failover is switching to a VM replica in case the original VM is damaged. You can fail over to the latest state of a replica or to any of its good known restore points.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the replica restore point to which you want to fail over. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Reason | Specifies the reason for performing a failover. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Planned | Performs planned failover. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Failing Over to Latest Restore Point of Replica [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to fail over to the WebServer\_replica VM replica to its latest restore point.  |  | | --- | | Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1 | Start-VBRReplicaFailover -Reason "Configuration recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. 2. Filter restore points with the Sort-Object method by the creationtime property to get the most recent one. 3. Pipe the cmdlet output to the Select cmdlet. Specify the First parameter value. 4. Pipe the cmdlet output to the Start-VBRReplicaFailover cmdlet. Specify the Reason parameter value. Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Failing Over to Specific Restore Point of Replica [Using Variable]

|  |  |
| --- | --- |
| This example shows how to fail over to the WebServer\_replica VM replica to a specific restore point.  |  | | --- | | $WebServer\_replica\_restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica"  Start-VBRReplicaFailover -RestorePoint $WebServer\_replica\_restorepoint[0] -Reason "Data recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $WebServer\_replica\_restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the first restore point in the array).   1. Run the Start-VBRReplicaFailover cmdlet. Set the $WebServer\_replica\_restorepoint[0] variable as the RestorePoint parameter value. Specify the Reason parameter value. Provide the RunAsync parameter. |

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)


