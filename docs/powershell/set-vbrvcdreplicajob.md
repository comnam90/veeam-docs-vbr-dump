---
title: "Set-VBRvCDReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcdreplicajob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRvCDReplicaJob


Short Description

Modifies Cloud Director replication jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRvCDReplicaJob -Job <VBRvCDReplicaJob> [-SourceObject <IVcdItem[]>] [-Name <string>] [-Description <string>] [-ExcludedObject <IVcdItem[]>] [-SourceNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-TargetNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-MetadataRepository <CBackupRepository>] [-Suffix <string>] [-RestorePointsToKeep <int>] [-RepositorySeed <CBackupRepository>] [-OriginalVApp <CVcdVappItem[]>] [-ReplicaVApp <CVcdVappItem[]>] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>] [-SourceProxy <CViProxy[]>] [-TargetProxy <CViProxy[]>] [-SourceWanAccelerator <CWanAccelerator>] [-TargetWanAccelerator <CWanAccelerator>] [-ScheduleOptions <VBRServerScheduleOptions>] [-CompressionLevel <VBRCompressionLevel> {None | DedupeFriendly | Optimal | High | Extreme}] [-NotificationOptions <VBRNotificationOptions>] [-HighPriority]  [<CommonParameters>] |

Detailed Description

Modifies Cloud Director replication jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the Cloud Director replication jobs that you want to modify. | Accepts the VBRvCDReplicaJob object. To get this object, run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. | True | Named | True (ByValue) |
| SourceObject | Specifies an array of vApps that you want to replicate. | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| Name | Specifies the name that you want to assign to the VDC replication job. | String | False | Named | False |
| Description | Specifies the description that you want to assign to assign to the VDC replication job. | String | False | Named | False |
| ExcludedObject | Specifies an array of VM containers that you want to exclude from the VDC replication job. You can exclude the following types of Cloud Director source objects:   * Organization * Organization VDC * vApp | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| EnableNetworkMapping | Enables network mapping. | SwitchParameter | False | Named | False |
| SourceNetwork | For the network mapping option.  Specifies an array of the production networks, to which the VMs in the job are connected.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For the network mapping option.  Specifies the network in the Disaster Recovery site. The replicated VMs will be connected to these networks.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| MetadataRepository | Specifies a backup repository that will store metadata for VDC replicas. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that the cmdlet will add to the name of VDC replicas.  Default: "\_replica". | String | False | Named | False |
| RestorePointsToKeep | Specifies a number of restore points you want to keep for of VDC replicas.  Permitted values: 1 to 28.  Default: 7. | Int | False | Named | False |
| EnableInitialSeeding | Enables replica seeding. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository that keeps a full backup of a VM that you want to replicate. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableReplicaMapping | Enables replica mapping. | SwitchParameter | False | Named | False |
| OriginalVApp | For replica mapping.  Specifies a production vApp that you want to replicate using replica mapping.  The VDC replication job will map this vApp to the vApp on the disaster recovery site.  Use the ReplicaVApp parameter to specify the vApp on the disaster recovery site. | Accepts the CVcdVappItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| ReplicaVApp | For replica mapping.  Specifies a vApp on the disaster recovery site. The cmdlet will map the production vApp to this vApp, and the VDC replication job will replicate data to this vApp.  Use the OriginalVApp parameter to specify the production vApp. | Accepts the CVcdVappItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| EnableGuestProcessing | Enables guest processing options. | SwitchParameter | False | Named | False |
| GuestProcessingOptions | Specifies guest processing options of a VDC replication job. | Accepts the VBRReplicaApplicationProcessingOptions object. To get this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies an array of the source proxies. The cmdlet will assign these proxies to the VDC replication job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md)cmdlet. | False | Named | False |
| TargetProxy | Specifies an array of the target proxies. The cmdlet will assign these proxies to the VDC replication job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md)cmdlet. | False | Named | False |
| EnableWanAccelerators | Enables the WAN accelerator option. | SwitchParameter | False | Named | False |
| SourceWanAccelerator | Specifies the WAN accelerator configured in the source site. The cmdlet will use this WAN accelerator data transfer.  Default: Not set. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| TargetWanAccelerator | Specifies the WAN accelerator configured in the target site. The cmdlet will use this WAN accelerator data transfer.  Default: Not set. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| EnableScheduleOptions | Enables schedule for a VDC replication job. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies a schedule for a VDC replication job. | Accepts the VBRServerScheduleOptions object. To get this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| CompressionLevel | Specifies the compression level of the replicated data:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Optimal. | VBRCompressionLevel | False | Named | False |
| NotificationOptions | Specifies notification options of a VDC replication job. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDReplicaJob object that defines settings of the VDC replication jobs.

Examples

Modifying VDC Replicas Metadata Repository

This example shows how to assign the Repository08 metadata repository to the Win20049 VDC replication job.

|  |
| --- |
| $job = Get-VBRvCDReplicaJob -Name "Win20049"  $repository = Get-VBRBackupRepository -Name "Repository08"  Set-VBRvCDReplicaJob -Job $job -MetadataRepository $repository |

Perform the following steps:

1. Run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
3. Run the Set-VBRvCDReplicaJob cmdlet. Set the $job variable as the Job parameter value. Set the $repository variable as the MetadataRepository parameter value.

Related Commands

* [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)


