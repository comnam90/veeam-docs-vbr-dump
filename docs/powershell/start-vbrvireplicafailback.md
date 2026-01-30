---
title: "Start-VBRViReplicaFailback"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvireplicafailback.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Start-VBRViReplicaFailback


Short Description

Fails back VMware VMs to production host.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Fail back from a replica to the original VM.

|  |
| --- |
| Start-VBRViReplicaFailback -RestorePoint <COib> [-Complete] [-StoragePolicyAction {Current | Stored | Default}] [-PowerOn] [-ReIp] [-SkipTagsRestore] [-DRSiteProxy <CViProxy[]>] [-ProdSiteProxy <CViProxy[]>] [-Reason <string>] [-QuickRollback] [-Force] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-SwitchToProduction] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Fail back from a replica to a VM recovered from a replica to a new location, or to any location but with different settings. The VM will be recovered from the replica during the failback process.

|  |
| --- |
| Start-VBRViReplicaFailback -RestorePoint <COib> [-Complete] -Server <CHost> [-ResourcePool <CViResourcePoolItem>] [-Datastore <VBRViDatastoreBase>] [-Folder <CViFolderItem>] [-StoragePolicy <VBRViStoragePolicy>] [-Network <VBRViNetworkInfo[]>] [-PowerOn] [-ReIp] [-SkipTagsRestore] [-DRSiteProxy <CViProxy[]>] [-ProdSiteProxy <CViProxy[]>] [-Reason <string>] [-QuickRollback] [-Force] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-SwitchToProduction] [-RunAsync] [-VmName <String>] [-WhatIf] [-Confirm]   [<CommonParameters>] |

* Fail back from a replica to a VM already recovered to a new location. This VM must be recovered before you perform failback. For example, you can recover the VM from a backup.

|  |
| --- |
| Start-VBRViReplicaFailback -RestorePoint <COib> [-Complete] -Vm <CViVmItem> [-PowerOn] [-ReIp] [-SkipTagsRestore] [-DRSiteProxy <CViProxy[]>] [-ProdSiteProxy <CViProxy[]>] [-Reason <string>] [-QuickRollback] [-Force] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-SwitchToProduction] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet fails back VMware VMs to the production host. This cmdlet finalizes the replica failover started with the [Start-VBRViReplicaFailover](start-vbrvireplicafailover.md) cmdlet.

Run the [Stop-VBRReplicaFailover](stop-vbrreplicafailover.md) cmdlet to undo failover.

Run the [Stop-VBRViReplicaFailback](stop-vbrvireplicafailback.md) cmdlet to undo failback.

|  |
| --- |
| Note: |
| The cmdlet will not run if the geographic location of the VMs you want to fail back and the target production host location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the replica restore point. The cmdlet uses this restore point to identify the replica you want to fail back. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, |
| Complete | Defines that the failback will be committed. | SwitchParameter | False | Named | False |
| StoragePolicyAction | Specifies the strategy for selecting storage policy profile in case the storage profile of the backed up VM differs from the profile of the original VM.   * Current: the restored VM will be subscribed to the same profile as in backup (if such profile still exists) or to the profile to which the original VM is subscribed (if profile as in backup was removed). * Default: the restored VM will be subscribed to the profile that is set as default for the target datastore. * Stored: the restored VM will be subscribed to the profile as in backup (if such profile still exists). | VBRStoragePolicyAction | False | Named | False |
| Server | For performing failback to a new location or to any location but with different settings.  Specifies the ESXi host where you want to register the recovered VM. | Accepts the Object object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| ResourcePool | For performing failback to a new location or to any location but with different settings.  Specifies the resource pool where you want to register the recovered VM.  If not specified, the cmdlet will use the resource pool that is set as default for the target host. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Datastore | For performing failback to a new location or to any location but with different settings.  Specifies the datastore where you want to register the recovered VM.  If not specified, the cmdlet will use the datastore that is set as default for the target host. | Accepts the VBRViDatastoreBase object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Folder | For performing failback to a new location or to any location but with different settings.  Specifies the folder where you want to register the recovered VM.  If not specified, the cmdlet will use the folder that is set as default for the target host. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| StoragePolicy | For performing failback to a new location or to any location but with different settings.  Specifies the storage policy with which you want to register the recovered VM.  If not specified, the cmdlet will use the storage policy that is set as default for the target host. | Accepts the VBRViStoragePolicy object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| Network | For performing failback to a new location or to any location but with different settings.  Specifies the array of production site networks. The cmdlet will map the replica to these networks. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| Vm | For performing failback to a new location.  Specifies the VM restored from backup. The cmdlet will map the replica to this VM. | Accepts the CViVmItem object. To get this object, run the  cmdlet. | True | Named | False |
| PowerOn | Defines that the production VM will be powered on after the failback. Otherwise, you will need to power the VM on manually. | SwitchParameter | False | Named | False |
| ReIp | Defines that the production VM will use the re-IP rules set in the replication job.  Do not enable the re-IP if the re-IP rules are not configured in the replication job. | SwitchParameter | False | Named | False |
| SkipTagsRestore | Defines that the VM will be restored without its VMware tag. Otherwise, the restored VM will keep its original tag. | SwitchParameter | False | Named | False |
| DRSiteProxy | Specifies the proxy configured on the disaster recovery site. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| ProdSiteProxy | Specifies the proxy configured on the production site. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason for performing failback. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete.  Note: This parameter cannot be used if you set the failback switch  schedule by running the [New-VBRFailbackSwitchingSchedule](new-vbrfailbackswitchingschedule.md) cmdlet to the Auto or Scheduled types. | SwitchParameter | False | Named | False |
| VmName | For performing failback to a new location or to any location but with different settings.  Specifies the name of the VM. The cmdlet will recover a VM with this name and will perform failback of the replica to this VM.  If not specified, the cmdlet will use the name of the original VM. | String | String | False | Named |
| QuickRollback | Defines that the cmdlet will perform incremental failback.  Note: Incremental failback uses VM changed block tracking data. If the cmdlet fails to retrieve the changed block tracking data for some reason, it will perform full VM failback. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform failback even if the geographic location of the VMs you want to fail back and the target production host location do not match. | SwitchParameter | False | Named | False |
| SwitchToProduction | Defines that the cmdlet will switch a VM replica from the Ready to switch state to the Failback state. | SwitchParameter | False | Named | False |
| SwitchingSchedule | Specifies a switching schedule for a VM replica. The cmdlet will switch the replica to the production VM according to this schedule. | Accepts the VBRFailbackSwitchingSchedule object. To create this object, run the [New-VBRFailbackSwitchingSchedule](new-vbrfailbackswitchingschedule.md) cmdlet. | False | Named | False |
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
| This example shows how to fail back to the original VM. The VM will fail back with the following parameters:   * The storage policy is set to Current. * The cmdlet will power the VM on after failback. * The cmdlet will perform failback using changed block tracking data.   |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1  Start-VBRViReplicaFailback -RestorePoint $restorepoint -StoragePolicyAction Current -PowerOn -QuickRollback |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter restore points with Sort-Object method by the creationtime property to get the most recent one. Save the result to the $restorepoint variable. 2. Run the Start-VBRViReplicaFailback cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the Current value as the StoragePolicyAction parameter value. * Provide the PowerOn and QuickRollback parameters. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failback to VM Reatored in New Location

|  |  |
| --- | --- |
| This example shows how to fail back to the VM restored in a new location.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1  $vm = Find-VBRViEntity -Name "Fileserver03"  Start-VBRViReplicaFailback -RestorePoint $restorepoint -VM $vm |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter restore points with Sort-Object method by the creationtime property to get the most recent one. Save the result to the $restorepoint variable. 2. Run the [Find-VBRViEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable. 3. Run the Start-VBRViReplicaFailback cmdlet. Set the $restorepoint as the RestorePoint parameter value. Set the $vm variable as the VM parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Failback to New Location

|  |  |
| --- | --- |
| This example shows how to fail back to a new location.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1  $srv = Get-VBRServer -Name "tech.qa.local"  Start-VBRViReplicaFailback -RestorePoint $restorepoint -Server $srv -PowerOn |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter restore points with Sort-Object method by the creationtime property to get the most recent one. Save the result to the $restorepoint variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $srv variable. 3. Run the Start-VBRViReplicaFailback cmdlet. Set the $restorepoint as the RestorePoint parameter value. Set the $srv variable as the Server parameter value. Provide the PowerOn parameter if you want the cmdlet to power on the VM after the failback. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrhventity.md)
* [Get-VBRLocation](get-vbrlocation.md)


