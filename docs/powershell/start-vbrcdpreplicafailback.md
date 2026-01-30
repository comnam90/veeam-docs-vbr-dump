---
title: "Start-VBRCDPReplicaFailback"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcdpreplicafailback.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Start-VBRCDPReplicaFailback


Short Description

Starts to perform failback from a CDP replica to the production VM.

Applies

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start to perform failback from a CDP replica to the original VM.

|  |
| --- |
| Start-VBRCDPReplicaFailback -Replica <VBRCDPReplica> [-DRProxy <VBRCDPProxy[]>] [-ProductionProxy <VBRCDPProxy[]>] [-Complete] [-SwitchToProduction] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-Reason <string>] [-PowerOn] [-IncludeTags] [-QuickRollback] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Start to perform failback from a CDP replica to a VM already recovered to a new location. This VM must be recovered before you perform failback. For example, you can recover the VM from a backup.

|  |
| --- |
| Start-VBRCDPReplicaFailback -Replica <VBRCDPReplica> -DestinationVM <CViVmItem> [-DRProxy <VBRCDPProxy[]>] [-ProductionProxy <VBRCDPProxy[]>] [-Complete] [-SwitchToProduction] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-Reason <string>] [-PowerOn] [-IncludeTags] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Start to perform failback from a CDP replica to a VM recovered from a replica to a new location, or to any location but with different settings. The VM will be recovered from the replica during the failback process.

|  |
| --- |
| Start-VBRCDPReplicaFailback -Replica <VBRCDPReplica> -Server <Object> [-DRProxy <VBRCDPProxy[]>] [-ProductionProxy <VBRCDPProxy[]>] [-Complete] [-SwitchToProduction] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-Reason <string>] [-PowerOn] [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Datastore <VBRViDatastoreBase>] [-DRNetwork <VBRViNetworkInfo[]>] [-ProductionNetwork <VBRViNetworkInfo[]>] [-IncludeTags] [-RunAsync] [-Force] [-VmName <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet starts to perform failback from CDP replica to the production VM. The CPD replica must be in the failover status. After you start to commit failback, the cmdlet switches the status of the CDP replica from the Fialover state to the Ready to switch state.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies a CDP replica from which you want to perform failback. | Accepts the VBRCDPReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| DestinationVM | For performing failback to a new location.  Specifies a VM that is restored in a different location. The cmdlet will perform failback from the CDP replica to this VM. | Accepts the CViVmItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| Server | For performing failback to a new location or to any location but with different settings.  Specifies an ESXi host or cluster. The cmdlet will perform failover of the CDP replica to a VM that will be recovered on this ESXi host or cluster. | Accepts the Object object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| DRProxy | Specifies an array of CDP proxies that are configured on the disaster recovery site. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| ProductionProxy | Specifies an array of CDP proxies that are configured on the production site. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| Complete | Defines that the cmdlet will switch the CDP replica from the failback state to the permanent failback state.  Note: Do not use this parameter if the PowerOn parameter is specified. Otherwise, the cmdlet will not work. | SwitchParameter | False | Named | False |
| SwitchToProduction | Defines that the cmdlet will switch the CDP replica from the ready to switch state to the failback state. | SwitchParameter | False | Named | False |
| SwitchingSchedule | Specifies a switching schedule for the CDP replica. The cmdlet will switch the replica to the production VM according to this schedule. | Accepts the VBRFailbackSwitchingSchedule object. To create this object, run the [New-VBRFailbackSwitchingSchedule](new-vbrfailbackswitchingschedule.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason for performing failback. | String | False | Named | False |
| ResourcePool | For performing failback to a new location or to any location but with different settings.  Specifies a resource pool. The cmdlet will perform failback of the CDP replica to a VM that will be recovered to this resource pool.  If you do not specify this parameter, the cmdlet will use the resource pool that is set as a default for the target host. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Folder | For performing failback to a new location or to any location but with different settings.  Specifies a folder. The cmdlet will perform failback of the CDP replica to a VM that will be recovered to this folder.  If you do not specify this parameter, the cmdlet will use the folder that is set as a default for the target host. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Datastore | For performing failback to a new location or to any location but with different settings.  Specifies the datastore. The cmdlet will perform failback of the CDP replica to a VM that will be recovered to this datastore.  If not specified, the cmdlet will use the datastore that is set as default for the target host. | Accepts the VBRViDatastoreBase object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| DRNetwork | For performing failback to a new location or to any location but with different settings.  Specifies an array of disaster recovery site networks. The cmdlet will map replica to these networks. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| ProductionNetwork | For performing failback to a new location or to any location but with different settings.  Specifies an array of production site networks. The cmdlet will map the replica to these networks. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| PowerOn | Defines that the cmdlet will power on a production VM after failback. If you do not provide this parameter, you will need to power the VM on manually.  Default: False.  Note: Do not use this parameter if the Complete parameter is specified. Otherwise, the cmdlet will not work. | SwitchParameter | False | Named | False |
| IncludeTags | Defines that the cmdlet will restore VMs with their VMware tags. If you do not provide this paramer,  the cmdlet will restore VMs without their VMware tag. | SwitchParameter | False | Named | False |
| QuickRollback | For performing failback to the original VM.  Defines that the cmdlet will perform incremental failback.  Note: Incremental failback uses VM changed block tracking data. If the cmdlet fails to retrieve the changed block tracking data for some reason, it will perform full VM failback. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete.  Note: This parameter cannot be used if you set the failback switch schedule by running the [New-VBRFailbackSwitchingSchedule](new-vbrfailbackswitchingschedule.md) cmdlet to the Auto or Scheduled types. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will fail back without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| VmName | For performing failback to a new location or to any location but with different settings.  Specifies the name of the VM. The cmdlet will recover a VM with this name and will perform failback of the CDP replica to this VM.  If not specified, the cmdlet will use the name of the original VM. | String | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Failback from CDP Replica to Orignal VM

|  |  |
| --- | --- |
| This example shows how to perform failback from the Win05 CDP replica to the original VM with the following settings:   * The cmdlet will use the Proxy05, Proxy07, Proxy09 machines as CDP proxies that are configured on the disaster recovery site. * The cmdlet will use the Proxy12, Proxy13, Proxy15 machines as CDP proxies that are configured on the production site.   |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win05"  $DRproxy = Get-VBRCDPProxy -Name "Proxy05, Proxy07, Proxy09"  $prodproxy = Get-VBRCDPProxy -Name "Proxy12, Proxy13, Proxy15"  Start-VBRCDPReplicaFailback -Replica $replica -DRProxy $DRproxy -ProductionProxy $prodproxy |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $DRproxy variable. 3. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $prodproxy variable. 4. Run the Start-VBRCDPReplicaFailback cmdlet. Specify the following settings:  * Set the $replica variable as the Replica parameter value. * Set the $DRproxy variable as the DRProxy parameter value. * Set the $prodproxy variable as the ProductionProxy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failback from CDP Replica to Different Location

|  |  |
| --- | --- |
| This example shows how to perform failback from the Win05 CDP replica to the Win05\_Prod VM. This VM is restored on the ESXiHost 04 ESXi host.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win05"  $server = Get-VBRServer -Name "ESXiHost 04"  $originalvm = Find-VBRViEntity -Server $server -Name "Win05\_Prod"  Start-VBRCDPReplicaFailback -Replica $replica -DestinationVM $originalvm |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Get the original VM:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $originalvm variable.  1. Run the Start-VBRCDPReplicaFailback cmdlet. Set the $replica variable as the Replica parameter value. Set the $originalvm variable as the DestinationVM parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Failback from CDP Replica with Different Settings

|  |  |
| --- | --- |
| This example shows how to perform failback from the Win05 CDP replica to the Win07\_Prod VM. The Win07\_Prod VM is restored during failback to the Resources resource pool and the ProductionRestored folder.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win05"  $server = Get-VBRServer -Name "ESXiHost 03"  $pool = Find-VBRViEntity -Server $server -ResourcePools -Name "Resources"  $folder = Find-VBRViEntity -Server $server -Name "ProductionRestored"  Start-VBRCDPReplicaFailback -Replica $replica -Server $server -ResourcePool $pool -Folder $folder -VmName "Win07\_Prod" |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Get the server, resource pool and folder:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Server, ResourcePools and Name parameter value. Save the result to the $pool variable. 3. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Server and Name parameter value. Save the result to the $folder variable.  1. Run the Start-VBRCDPReplicaFailback cmdlet. Specify the following settings:  * Set the $replica variable as the Replica parameter value. * Set the $server variable as the Server parameter value. * Set the $pool variable as the ResourcePool parameter value. * Set the $folder variable as the Folder parameter value.  * Specify the Name parameter value. |

Related Commands

* [Get-VBRCDPReplica](get-vbrcdpreplica.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)


