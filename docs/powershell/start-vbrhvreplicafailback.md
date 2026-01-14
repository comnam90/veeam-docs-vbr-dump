---
title: "Start-VBRHvReplicaFailback"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrhvreplicafailback.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Start-VBRHvReplicaFailback

In this article

Short Description

Fails back Hyper-V VMs to production host.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Perform failback to the original VM.

|  |
| --- |
| Start-VBRHvReplicaFailback -RestorePoint <COib> [-Complete] [-PowerOn] [-Reason <string>] [-RunAsync] [-QuickRollback] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Perform failback to the original VM restored in a different location.

|  |
| --- |
| Start-VBRHvReplicaFailback -RestorePoint <COib> -Vm <CHvVmItem> [-PowerOn] [-Reason <string>] [-RunAsync] [-QuickRollback] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Perform failback to another location.

|  |
| --- |
| Start-VBRHvReplicaFailback -RestorePoint <COib> -Server <CHost> [-Datastore <string>] [-Network <VBRHvServerNetworkInfo[]>] [-VmName <string>] [-PreserveVmID] [-RegisterAsClusterResource] [-PowerOn] [-Reason <string>] [-RunAsync] [-QuickRollback] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet fails back Hyper-V VMs to the production host. This cmdlet finalizes the replica failover started with the [Start-VBRHvReplicaFailover](start-vbrhvreplicafailover.md) cmdlet.

Run the [Stop-VBRReplicaFailover](stop-vbrreplicafailover.md) cmdlet to undo failover.

Run the [Stop-VBRHvReplicaFailback](stop-vbrhvreplicafailback.md) cmdlet to undo failback.

|  |
| --- |
| ![Start-VBRHvReplicaFailback](images/icon_note.webp) Note: |
| The cmdlet will not run if the geographic location of the VMs you want to fail back and the target production host location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the replica restore point. The cmdlet uses this restore point to identify the replica you want to fail back. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, |
| Complete | Defines that the failback will be committed. | SwitchParameter | False | Named | False |
| Server | Used for failback to another location.  Specifies the Hyper-V host where you want to register the VM. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Datastore | Used for failback to another location.  Specifies the path to the folder where you want to register the VM.  If not specified, the cmdlet will use the datastore that is set as default for the target host. | String | False | Named | False |
| Network | Used for failback to another location.  Specifies the array of production site networks. The cmdlet will map the replica to these networks. | Accepts the [VBRHvServerNetworkInfo](vbrhvservernetworkinfo.md) object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | False | Named | False |
| VmName | Used for failback to another location.  Specifies the name you want to assign to the new VM. | String | False | Named | False |
| PreserveVmID | Defines that the restored VM will get the ID of the original VM. Otherwise, the restored VM will get a new ID. | SwitchParameter | False | Named | False |
| RegisterAsClusterResource | Defines that the VM will be registered as a part of Microsoft Failover Cluster. | SwitchParameter | False | Named | False |
| Vm | Used for failback to the original VM restored in a different location.  Specifies the VM restored from backup. The cmdlet will map the replica to this VM. | Accepts the CHvVmItem object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | True | Named | False |
| PowerOn | Defines that the production VM will be powered on after the failback. Otherwise, you will need to power the VM on manually. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing failback. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| QuickRollback | Defines that the cmdlet will perform incremental failback.  Note:  Incremental failback uses VM changed block tracking data. If the cmdlet fails to retrieve the changed block tracking data for some reason, it will perform full VM failback. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform failback even if the geographic location of the VMs you want to fail back and the target production host location do not match. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Failback to Original VM

|  |  |
| --- | --- |
| This example shows how to failback to the original VM.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1  Start-VBRHvReplicaFailback -RestorePoint $restorepoint -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter restore points with the Sort-Object method by the creationtime property to get the most recent one. Save the result to the $restorepoint variable. 2. Run the Start-VBRHvReplicaFailback cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failback to Original VM in Different Location

|  |  |
| --- | --- |
| This example shows how to failback to the original VM restored in a different location.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1  $vm = Find-VBRHvEntity -Name "Fileserver02"  Start-VBRHvReplicaFailback -RestorePoint $restorepoint -VM $vm |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter restore points with the Sort-Object method by the creationtime property to get the most recent one. Save the result to the $restorepoint variable. 2. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable. 3. Run the Start-VBRHvReplicaFailback cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $vm variable as the VM parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Failback to Another Location

|  |  |
| --- | --- |
| This example shows how to failback to another location.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1  $srv =  Get-VBRServer -Name "tech.support.local"  Start-VBRHvReplicaFailback -RestorePoint $restorepoint -Server $srv -VmName "Webserver\_N" -QuickRollback |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter restore points with the Sort-Object method by the creationtime property to get the most recent one. Save the result to the $restorepoint variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $srv variable. 3. Run the Start-VBRHvReplicaFailback cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $srv variable as the Server parameter value. * Specify the VmName parameter value. * Provide the QuickRollback parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Find-VBRHvEntity](find-vbrhventity.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRLocation](get-vbrlocation.md)

Page updated 6/27/2024

Page content applies to build 13.0.1.1071
