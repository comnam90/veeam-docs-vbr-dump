---
title: "Add-VBRvCDReplicaJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcdreplicajob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRvCDReplicaJob

In this article

Short Description

Creates Cloud Director replication jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRvCDReplicaJob -SourceObject <IVcdItem[]> -OrganizationVdc <CVcdOrganizationVdcItem> [-Name <string>] [-Description <string>] [-ExcludedObject <IVcdItem[]>] [-GeneralStoragePolicy <CVcdOrgVdcStorageProfile>] [-IndividualVAppStoragePolicy <VBRvCDIndividualObjectStoragePolicy[]>] [-SourceNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-TargetNetwork <VBRvCDOrgVdcNetworkInfo[]>] [-MetadataRepository <CBackupRepository>] [-Suffix <string>] [-RestorePointsToKeep <int>] [-RepositorySeed <CBackupRepository>] [-OriginalVApp <CVcdVappItem[]>] [-ReplicaVApp <CVcdVappItem[]>] [-GuestProcessingOptions <VBRReplicaApplicationProcessingOptions>] [-SourceProxy <CViProxy[]>] [-TargetProxy <CViProxy[]>] [-SourceWanAccelerator <CWanAccelerator>] [-TargetWanAccelerator <CWanAccelerator>] [-ScheduleOptions <VBRServerScheduleOptions>] [-CompressionLevel <VBRCompressionLevel> {None | DedupeFriendly | Optimal | High | Extreme}] [-NotificationOptions <VBRNotificationOptions>] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet creates Cloud Director replication jobs.

Note that when you create a Cloud Director replication jobs, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRvCDReplicaJob](start-vbrvcdreplicajob.md) cmdlet to run the job manually.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceObject | Specifies an array of vApps that you want to replicate. | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| OrganizationVdc | Specifies the cloud organization VDC. The job will store the Cloud Director replicas on the selected organization VDC. | Accepts the CVcdOrganizationVdcItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |
| Name | Specifies the name that you want to assign to the VDC replication job. | String | False | Named | False |
| Description | Specifies the description that you want to assign to the VDC replication job. | String | False | Named | False |
| ExcludedObject | Specifies an array of VM containers that you want to exclude from the VDC replication job. You can exclude the following types of Cloud Director source objects:   * Organization * Organization VDC * vApp | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| GeneralStoragePolicy | Specifies the storage policy. The cmdlet will create VDC replication jobs according to the policy settings. | Accepts the CVcdOrgVdcStorageProfile object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| IndividualVAppStoragePolicy | Specifies the individual storage policy for a Cloud Director VM. The job will create VDC replicas of these VMs according to the policy settings. | Accepts the VBRvCDIndividualObjectStoragePolicy[] object. To create this object, run the [New-VBRvCDIndividualObjectStoragePolicy](new-vbrvcdindividualobjectstoragepolicy.md) cmdlet. | False | Named | False |
| SourceNetwork | For the network mapping option.  Specifies an array of the production networks, to which the vApps are connected.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For the network mapping option.  Specifies the network in the Disaster Recovery site. The replicated VMs will be connected to these networks.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDOrgVdcNetworkInfo[] object. To get this object, run the [Get-VBRVCDOrgVdcNetworkInfo](get-vbrvcdorgvdcnetworkinfo.md) cmdlet. | False | Named | False |
| MetadataRepository | Specifies a backup repository that will store metadata for VDC replicas. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that the cmdlet will add to the name of VDC replicas.  Default: "\_replica". | String | False | Named | False |
| RestorePointsToKeep | Specifies a number of restore points you want to keep for of VDC replicas.  Permitted values: 1 to 28.  Default: 7. | Int | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository that keeps a full backup of a VM that you want to replicate. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| OriginalVApp | For replica mapping.  Specifies a production vApp that you want to replicate using replica mapping.  The VDC replication job will map this vApp to the vApp on the disaster recovery site.  Use the ReplicaVApp parameter to specify the vApp on the disaster recovery site. | Accepts the CVcdVappItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| ReplicaVApp | For replica mapping.  Specifies a vApp on the disaster recovery site. The cmdlet will map the production vApp to this vApp, and the VDC replication job will replicate data to this vApp.  Use the OriginalVApp parameter to specify the production vApp. | Accepts the CVcdVappItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| GuestProcessingOptions | Specifies guest processing options of a VDC replication job. | Accepts the VBRReplicaApplicationProcessingOptions object. To create this object, run the [New-VBRReplicaApplicationProcessingOptions](new-vbrreplicaapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies an array of the source proxies. The cmdlet will assign these proxies to the VDC replication job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies an array of the target proxies. The cmdlet will assign these proxies to the VDC replication job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| SourceWanAccelerator | Specifies the WAN accelerator configured in the source site. The cmdlet will use this WAN accelerator data transfer.  Default: Not set. | CWanAccelerator | False | Named | False |
| TargetWanAccelerator | Specifies the WAN accelerator configured in the target site. The cmdlet will use this WAN accelerator data transfer.  Default: Not set. | CWanAccelerator | False | Named | False |
| ScheduleOptions | Specifies a schedule for a VDC replication job. | Accepts the VBRServerScheduleOptions object. To get this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| CompressionLevel | Specifies the compression level of the replicated data:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Optimal. | VBRCompressionLevel | False | Named | False |
| NotificationOptions | Specifies notification options of a VDC replication job. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | False | Named | False | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDReplicaJob object that defines settings of the VDC replication jobs.

Examples

Creating VDC Replication Job

This example shows how to create the vCD\_05j VDC replication job to replicate the AvP04 vApp to the Org07 organization VDC.

|  |
| --- |
| $vapp = Find-VBRvCloudEntity -Name "AvP04" -VApp  $orgvdc = Find-VBRvCloudEntity -Name "Org07" -OrganizationVdc  Add-VBRvCDReplicaJob -SourceObject $vapp -OrganizationVdc $orgvdc -Name "vCD\_05j" -Description "AvP04 replica" |

Perform the following steps:

1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name parameter value. Save the result to the $vapp variable.
2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name parameter value. Provide the OrganizationVdc parameter. Save the result to the $orgvdc variable.
3. Run the Add-VBRvCDReplicaJob cmdlet. Specify the following settings:

* Set the $vapp variable as the SourceObject parameter value.
* Set the $orgvdc variable as the OrganizationVdc parameter value.
* Specify the Name parameter value.
* Specify the Description parameter value.

Related Commands

[Find-VBRvCloudEntity](find-vbrvcloudentity.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
