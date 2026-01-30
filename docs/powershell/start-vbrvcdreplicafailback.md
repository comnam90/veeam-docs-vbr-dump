---
title: "Start-VBRvCDReplicaFailback"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcdreplicafailback.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Start-VBRvCDReplicaFailback


Short Description

Starts to perform failback from Cloud Director replica to the production VM.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Starts to perform failback from a Cloud Director replica to the original vApp.

|  |
| --- |
| Start-VBRvCDReplicaFailback -RestorePoint <COib> [-Complete] [-Retry] [-SwitchToProduction] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-Reason <string>] [-PowerOn] [-DRSiteProxy <CViProxy[]>] [-ProdSiteProxy <CViProxy[]>] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Starts to perform failback from a Cloud Director replica to the original vApp that is restored in a different location.

|  |
| --- |
| Start-VBRvCDReplicaFailback -RestorePoint <COib> -DestinationvApp <CVcdVappItem> [-Complete] [-Retry] [-SwitchToProduction] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-Reason <string>] [-PowerOn] [-DRSiteProxy <CViProxy[]>] [-ProdSiteProxy <CViProxy[]>] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Starts to perform failback from a Cloud Director replica to the production vApp in a different location or with different settings.

|  |
| --- |
| Start-VBRvCDReplicaFailback -RestorePoint <COib> -OrganizationvDC <CVcdOrganizationVdcItem> [-Complete] [-Retry] [-SwitchToProduction] [-SwitchingSchedule <VBRFailbackSwitchingSchedule>] [-Reason <string>] [-PowerOn] [-DestinationVAppName <string>] [-StoragePolicy <CVcdOrgVdcStorageProfile>] [-ReplicaNetwork <IVBRServerNetworkInfo[]>] [-DestinationNetwork <IVBRServerNetworkInfo[]>] [-DRSiteProxy <CViProxy[]>] [-ProdSiteProxy <CViProxy[]>] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet performs failback from a Cloud Director replica to the production vApp.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of a Cloud Director replica to which you want to perform a fail back. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| DestinationvApp | Specifies the vApp to which you want to perform a fail back. | Accepts the CVcdVappItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |
| OrganizationvDC | Specifies the organization VDC to which you want to perform a fail back. | Accepts the CVcdOrganizationVdcItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| Complete | Defines that the cmdlet will switch the VDC replica from the failback state to the permanent failback state. | SwitchParameter | False | Named | False |
| Retry | Defines that if failback does not complete successfully, Veeam Backup & Replication will start to perform failback to a VDC replica again.  If you do not specify this parameter, the cmdlet will not start to perform failover to a VDC replica if some VMs are in the incomplete state. | SwitchParameter | False | Named | False |
| SwitchToProduction | Defines that the cmdlet will switch the VDC replica from the ready to switch state to the failback state. | SwitchParameter | False | Named | False |
| SwitchingSchedule | Specifies a switching schedule for VDC replica. The cmdlet will switch the replica to the production VM according to this schedule. | Accepts the VBRFailbackSwitchingSchedule object. To create this object, run the [New-VBRFailbackSwitchingSchedule](new-vbrfailbackswitchingschedule.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason for performing failback. | String | False | Named | False |
| PowerOn | Defines that the cmdlet will power on the production VM after performing failback. If you do not provide this parameter, you will need to power the VM on manually. | SwitchParameter | False | Named | False |
| DestinationVAppName | Specifies a name of a new vApp. The cmdlet will create a vApp with this name and will perform failback to this vApp. | String | False | Named | False |
| StoragePolicy | Specify the storage policy that you want to apply to the production VMs after performing failback. | Accepts the CVcdOrgVdcStorageProfile object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| ReplicaNetwork | Specifies an array of the VDC replica networks for Cloud Director replica mapping. | Accepts the IVBRServerNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| DestinationNetwork | Specifies an array of the target VDC replica networks for Cloud Director replica mapping. | Accepts the IVBRServerNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| DRSiteProxy | For failback to a different location.  Specifies an array of disaster recovery site networks. The cmdlet will map the replica to these networks. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| ProdSiteProxy | For failback to a different location.  Specifies an array of production site networks. The cmdlet will map the replica to these networks. | Accepts the VBRCDPProxy[] object. To get this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete.  Note: This parameter cannot be used if you set the failback switch  schedule by running the [New-VBRFailbackSwitchingSchedule](new-vbrfailbackswitchingschedule.md) cmdlet to the Auto or Scheduled types. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform failover without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

Guid.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Failback from Cloud Director Replica to Original Location

|  |  |
| --- | --- |
| This example shows how to perform failback of the VirginiaVMs Cloud Director replica to the original VM.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "VirginiaVMs"  Start-VBRvCDReplicaFailback -RestorePoint $restorepoint -Retry |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCDReplicaFailback cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Provide the Retry parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Failback from Cloud Director Replica to Different vApp

|  |  |
| --- | --- |
| This example shows how to perform failback of the VirginiaVMs Cloud Director replica to the Atlanta vApp.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "VirginiaVMs"  $vapp = Find-VBRvCloudEntity -VApp -Name "Atlanta"  Start-VBRvCDReplicaFailback -RestorePoint $restorepoint -DestinationvApp $vapp |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the VApp and Name parameter values. Save the result to the $vapp variable. 3. Run the Start-VBRvCDReplicaFailback cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $vapp variable as the DestinationvApp parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Failback from Cloud Director Replica to Different Organization VDC

|  |  |
| --- | --- |
| This example shows how to perform failback of the VirginiaVMs Cloud Director replica to the Virginia organization VDC  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "VirginiaVMs"  $organization = Find-VBRvCloudEntity -Name "Virginia" -OrganizationVdc  Start-VBRvCDReplicaFailback -RestorePoint $restorepoint -OrganizationvDC $organization |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the OrganizationVdc and Name parameters. Save the result to the $organization variable. 3. Run the Start-VBRvCDReplicaFailback cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $organization variable as the OrganizationvDC parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)


