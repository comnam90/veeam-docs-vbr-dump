---
title: "Start-VBRvCDCDPReplicaFailback"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcdcdpreplicafailback.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Start-VBRvCDCDPReplicaFailback


Short Description

Starts to perform failback from a Cloud Director CDP replica to the production vApp.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start to perform failback from a Cloud Director CDP replica to the original vApp.

|  |
| --- |
| Start-VBRvCDCDPReplicaFailback -Replica <VBRvCDCDPReplica> [-DRProxy <VBRCDPProxy[]>] [-ProductionProxy <VBRCDPProxy[]>] [-Complete] [-SwitchToProduction] [-Retry] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-Reason <string>] [-PowerOn] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Start to perform failback from a Cloud Director CDP replica to the original vApp that is already recovered to a new location.

|  |
| --- |
| Start-VBRvCDCDPReplicaFailback -Replica <VBRvCDCDPReplica> -DestinationvApp <CVcdVappItem> [-DRProxy <VBRCDPProxy[]>] [-ProductionProxy <VBRCDPProxy[]>] [-Complete] [-SwitchToProduction] [-Retry] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-Reason <string>] [-PowerOn] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Start to perform failback from a Cloud Director CDP replica to a different location or with different settings.

|  |
| --- |
| Start-VBRvCDCDPReplicaFailback -Replica <VBRvCDCDPReplica> -OrganizationvDC <CVcdOrganizationVdcItem> [-DRProxy <VBRCDPProxy[]>] [-ProductionProxy <VBRCDPProxy[]>] [-Complete] [-SwitchToProduction] [-Retry] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-DestinationVAppName <string>] [-StoragePolicy <CVcdOrgVdcStorageProfile>] [-DRNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-ProductionNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-Reason <string>] [-PowerOn] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet starts to perform failback from a Cloud Director CDP replica to the production vApp. The replica must be in the Failover state. After you start to commit failback, the cmdlet switches the state of the replica from Failover to Ready to switch.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies the replica from which you want to fail back. | Accepts the VBRvCDCDPReplica object. To get this object, run the [Get-VBRCDPReplica](get-vbrcdpreplicavcd.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| DestinationvApp | For performing failback to an already recovered vApp in a different location.  Specifies the original vApp that is restored in a different location. The cmdlet will perform failback from the replica to this vApp. | Accepts the CViVmItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| OrganizationvDC | For performing failback to a different location or with different settings.  Specifies the organization VDC where you want to restore the vApp from the specified replica. | Accepts the CVcdOrganizationVdcItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |
| DRProxy | Specifies an array of CDP proxies that are configured in the disaster recovery site and that will be used for failback. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| ProductionProxy | Specifies an array of CDP proxies that are configured in the production site and that will be used for failback. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| Complete | Defines that the cmdlet will commit failback. | SwitchParameter | False | Named | False |
| SwitchToProduction | Defines that the cmdlet will switch the replica from the Ready to switch state to the Failback state. | SwitchParameter | False | Named | False |
| Retry | Defines that if failback does not complete successfully, the cmdlet will start to perform failback to a replica again.  If you do not specify this parameter, the cmdlet will not start to perform failback if any vApps are in the incomplete state. | SwitchParameter | False | Named | False |
| SwitchingSchedule | Specifies a switching schedule. The cmdlet will switch the replica to the production vApp according to this schedule. | Accepts the VBRFailbackSwitchingSchedule object. To create this object, run the [New-VBRFailbackSwitchingSchedule](new-vbrfailbackswitchingschedule.md) cmdlet. | False | Named | False |
| DestinationVAppName | For performing failback to a different location or with different settings.  Specifies a name for the vApp that will be restored from the specified replica. The cmdlet will create a vApp with this name and will perform failback to this vApp. | String | False | Named | False |
| StoragePolicy | For performing failback to a different location or with different settings.  Specify the storage policy that you want to apply to the production vApp after performing failback. | Accepts the CVcdOrgVdcStorageProfile object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| DRNetwork | For performing failback to a different location or with different settings.  Specifies an array of networks in the disaster recovery site to which replica is connected. The cmdlet will map these networks to the networks in the production site.  Note: If you specify this parameter, you must also specify the ProductionNetwork parameter. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| ProductionNetwork | For performing failback to a different location or with different settings.  Specifies an array of networks in the production site. The cmdlet will restore the vApp from the specified replica and will map the replica networks to these networks.  Note: If you specify this parameter, you must also specify the DRNetwork parameter. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason for performing failback. | String | False | Named | False |
| PowerOn | Defines that the cmdlet will power on the production vApp after failback. If you do not provide this parameter, you will need to power on VMs in the vApp manually.  Default: False.  Note: If you provide this parameter with the Complete parameter, this parameter will not work. The VMs in the vApp will remain in the state it had before committing failback. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete.  Note: This parameter can be used if you set the failback switch schedule by running the [New-VBRFailbackSwitchingSchedule](new-vbrfailbackswitchingschedule.md) cmdlet to the Manual type. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will fail back without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

SessionId <Guid>

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Failback from Cloud Director CDP Replica to Original vApp

|  |  |
| --- | --- |
| This example shows how to start to perform failback from a Cloud Director CDP replica to the original vApp.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win07"  Start-VBRvCDCDPReplicaFailback -Replica $replica |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Start-VBRvCDCDPReplicaFailback cmdlet. Set the $replica variable as the Replica parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failback from Cloud Director CDP Replica to Original vApp in New Location

|  |  |
| --- | --- |
| This example shows how to start to perform failback from a Cloud Director CDP replica to the original vApp that is already recovered to a new location.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win07"  $server = Get-VBRServer -Name "Cloud Server"  $vapp = Find-VBRvCloudEntity -Server $server -VApp  Start-VBRvCDCDPReplicaFailback -Replica $replica -DestinationvApp $vapp |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Server and VApp parameters values. Save the result to the $vapp variable. 4. Run the Start-VBRvCDCDPReplicaFailback cmdlet. Set the $replica variable as the Replica parameter value.  Set the $vapp variable as the DestinationvApp parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Failback from Cloud Director CDP Replica to Different Location

|  |  |
| --- | --- |
| This example shows how to start to perform failback from a Cloud Director CDP replica to a different location.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "Win07"  $server = Get-VBRServer -Name "Cloud Server"  $organization = Find-VBRvCloudEntity -Server $server -OrganizationVdc  Start-VBRvCDCDPReplicaFailback -Replica $replica -OrganizationvDC $organization |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Server and OrganizationVdc parameters values. Save the result to the $organization variable. 4. Run the Start-VBRvCDCDPReplicaFailback cmdlet. Set the $replica variable as the Replica parameter value. Set the $organization variable as the OrganizationvDC parameter value. |

Related Commands

* [Get-VBRCDPReplica](get-vbrcdpreplica.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)


