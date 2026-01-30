---
title: "Set-VBRvCDCloudReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcdcloudreplicajob.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRvCDCloudReplicaJob


Short Description

Modifies Cloud Director cloud replication jobs.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRvCDCloudReplicaJob -Job <CBackupJob> [-Name <string>] [-Entity <IViItem[]>] [-OrganizationvDC <VBRvCDCloudOrganizationvDC>] [-vApp <VBRvCDCloudvApp>] [-StoragePolicy <VBRvCDCloudStoragePolicy>] [-Suffix <string>] [-BackupRepository <CBackupRepository>] [-Description <string>] [-EnableNetworkMapping] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRCloudServerNetworkInfo[]>] [-SourceProxy <CViProxy[]>] [-UseWANAccelerator] [-SourceWANAccelerator <CWanAccelerator>] [-SourceRepository <CBackupRepository[]>] [-DiskType <EDiskCreationMode> {Source | Thick | Thin | ThickEagerZeroed}] [-EnableSeeding] [-RepositorySeed <CBackupRepository>] [-EnableVMMapping] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <COib[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Cloud Director cloud replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the Cloud Director cloud replication job that you want to modify. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name that you want to assign to the cloud replication job | String | False | Named | False |
| Entity | Specifies an array of VMs.The cmdlet will add the selected VMs to the Cloud Director replication job. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | True (ByPropertyName) |
| OrganizationvDC | Specifies the cloud organization VDC. The job will store the replicas on the selected organization VDC. | Accepts the VBRvCDCloudOrganizationvDC object. To get this object, run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. | False | Named | False |
| vApp | Specifies the vApp container. The job will store the replicas on the selected vApp. | Accepts the VBRvCDCloudvApp object. To get this object, run the [Get-VBRvCDCloudvApp](get-vbrvcdcloudvapp.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the Cloud Director cloud storage policy. The job will create replicas per the policy settings. | Accepts the VBRvCDCloudStoragePolicy object. To get this object, run the [Get-VBRvCDCloudStoragePolicy](get-vbrvcdcloudstoragepolicy.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  If omitted, the replicated VMs will have the '\_replica' suffix by default. | String | False | Named | False |
| BackupRepository | Specifies the user backup repository that will be used to store replica metadata files.  If not set, the default backup repository will be used. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Description | Specifies the description of a new job. | String | False | Named | False |
| EnableNetworkMapping | Enables the network mapping option.  Use the following parameters to set the network mapping rules:   * SourceNetwork * TargetNetwork | SwitchParameter | False | Named | False |
| SourceNetwork | For the network mapping option.  Specifies an array of the production networks, to which the VMs in the job are connected.  Note: The number of the source and the target networks must be the same. | Accepts the [VBRViNetworkInfo[]](vbrvinetworkinfo.md) object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For the network mapping option.  Specifies an array of networks on the Disaster Recovery site. The replicated VMs will be connected to these networks.  Note: The number of the source and the target networks must be the same. | Accepts the VBRvCDCloudNetworkInfo[] object. To get this object, run the [Get-VBRvCDCloudNetworkInfo](get-vbrvcdcloudnetworkinfo.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the source proxy that will be used by the job. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| UseWANAccelerator | Defines that the data will be transferred via WAN accelerators.  Use the SourceWANAccelerator and TargetWANAccelerator parameters to set the pair of WAN accelerators. | SwitchParameter | False | Named | False |
| SourceWANAccelerator | Specifies the WAN accelerator configured in the source site that will be used for data transfer.  Note: You can set the source WAN accelerator only if the cloud provider has a target WAN accelerator configured. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| SourceRepository | Used for building a replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain.  Note: You cannot specify a cloud repository. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| DiskType | Specifies the format that will be used to restore replica disk files:     * Source: the restored replica disks will be the same format as source. * Thick: the restored replica disks will be thick. * Thin: the restored replica disks will be thin.   Default: Source. | EDiskCreationMode | False | Named | False |
| EnableSeeding | Enables the replication job to use seeding. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository where the seed (the full backup) resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableVMMapping | Enables the replication job to use replica mapping. | SwitchParameter | False | Named | False |
| OriginalVM | For replica mapping.  Specifies an array of production VMs that you want to replicate using replica mapping.  The replication job will map these VMs to selected replica VMs on the Disaster Recovery site.  Use the ReplicaVM parameter to specify the replica VM on the Disaster Recovery site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies an array of VMs on the Disaster Recovery site that you want to use as the replication target. The replication job will map the production VMs to these VMs.  Use the OriginalVM parameter to specify the production VM. | Accepts the VBRvCDCloudVM[] object. To get this object, run the [Get-VBRvCDCloudVM](get-vbrvcdcloudvm.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will modify the job even if the geographic location of the VMs added to the job and the target host location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

Modifying Organization VDC for Cloud Director Cloud Replication Job

This example shows how to change the organization VDC for the ReplicavCDJob Cloud Director cloud replication job to the AtlanateOrg organization VDC.

|  |
| --- |
| $replicaJob = Get-VBRJob -Name "ReplicavCDJob"  $vdc = Get-VBRvCDCloudOrganizationvDC -Name "AtlanateOrg"  Set-VBRvCDCloudReplicaJob -Job $replicajob -OrganizationvDC $vdc |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $replicaJob variable.
2. Run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. Specify the Name parameter value. Save the result to the $vdc variable.
3. Run the Set-VBRvCDCloudReplicaJob cmdlet. Set the $replicajob variable as the Job parameter value. Set the $vdc variable as the OrganizationvDC parameter value.

Related Command

* [Get-VBRJob](get-vbrvcdcloudorganizationvdc.md)
* [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md)


