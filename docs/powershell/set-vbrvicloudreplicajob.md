---
title: "Set-VBRViCloudReplicaJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvicloudreplicajob.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRViCloudReplicaJob

In this article

Short Description

Modifies a VMware cloud replication job.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViCloudReplicaJob -Job <CBackupJob> [-Name <string>] [-Entity <IViItem[]>] [-Datastore <VBRCloudDatastore>] [-Suffix <string>] [-BackupRepository <CBackupRepository>] [-Description <string>] [-EnableNetworkMapping] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRCloudServerNetworkInfo[]>] [-SourceProxy <CViProxy[]>] [-UseWANAccelerator] [-SourceWANAccelerator <CWanAccelerator>] [-SourceRepository <CBackupRepository[]>] [-DiskType <EDiskCreationMode> {Source | Thick | Thin | ThickEagerZeroed}] [-EnableSeeding] [-RepositorySeed <CBackupRepository>] [-EnableVMMapping] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <COib[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an existing VMware cloud replication job.

|  |
| --- |
| Note |
| Consider the following:   * The cmdlet will not run if the geographic location of the VMs added to the job and the target cloud host location do not match. If you still want to run the cmdlet, use the Force parameter. * To modify settings, specify new values for the necessary parameters. After you run this cmdlet, the previous settings will be rewritten with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the replication job you want to modify. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name you want to assign to the cloud replication job. | String | False | Named | False |
| Entity | Specifies the array of VMs you want to add to the job. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | True (ByProperty Name) |
| Datastore | Specifies the cloud datastore to which you want to replicate. | Accepts the [VBRCloudDatastore](vbrclouddatastore.md) object. To get this object, run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  If omitted, the replicated VMs will have the '\_replica' suffix by default. | String | False | Named | False |
| BackupRepository | Specifies the backup repository which will be used to store replica metadata files.  Default: default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Description | Specifies the description of the new job. | String | False | Named | False |
| EnableNetworkMapping | Enables the network mapping. Use the SourceNetwork and the TargetNetwork parameters to set the network mapping rules. | SwitchParameter | False | Named | False |
| SourceNetwork | Used to set the source network for the EnableNetworkMapping parameter.  Specifies the production network to which VMs added to the job are connected.  Note: the number of the source and the target networks must be the same. | Accepts the [VBRViNetworkInfo[]](vbrvinetworkinfo.md) object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | Used to set the target network for the EnableNetworkMapping parameter.  Specifies the network in the DR site to which VM replicas must be connected.  Note: the number of the source and the target networks must be the same. | Accepts the [VBRCloudServerNetworkInfo[]](vbrcloudservernetworkinfo.md) object. To get this object, run the [Get-VBRCloudServerNetworkInfo](get-vbrcloudservernetworkinfo.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the source proxy that will be used by the job.  Default: automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| UseWANAccelerator | Defines that the data must be transferred via WAN accelerators.  Use the SourceWANAccelerator parameter to set the WAN accelerator on the source side. | SwitchParameter | False | Named | False |
| SourceWANAccelerator | Specifies the WAN accelerator configured in the source site that will be used for data transfer.  Note: you can set the source WAN accelerator only if the cloud provider has a target WAN accelerator configured. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| SourceRepository | Used for building replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| DiskType | Specifies the disks that you want to replicate: Source, Thick, Thin.  Default: Source. | EDiskCreationMode | False | Named | False |
| EnableSeeding | Defines if replica seeding must be used for the replication job. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository on which a backup used as a seed for the replication job resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| EnableVMMapping | Enables the replication job to use replica mapping. | SwitchParameter | False | Named | False |
| OriginalVM | For replica mapping.  Specifies the production VM you want to replicate using replica mapping.  The replication job will map this VM to a selected replica VM on the DR site.  Use the ReplicaVM parameter to specify the replica VM on the DR site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| ReplicaVM | For replica mapping.  Specifies the VM on the DR site you want to use as the replication target. The replication job will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the COib[] object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Force | Defines that the cmdlet will modify the cloud replication job even if the geographic location of the VMs added to the job and the target cloud host location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Changing Cloud Datastore for Cloud Replica Job

This example shows how to apply custom settings to the cloud replica job named Cloud Replica Job.

|  |
| --- |
| $job = Get-VBRJob –Name “Cloud Replica Job”  $cloudServer = Get-VBRCloudServer -Name 104.45.95.227  $NewCloudDatastore = Get-VBRCloudDatastore -CloudServer $cloudServer –Name “CDEDatastore”  Set-VBRViCloudReplicaJob –Job $job –Datastore $NewCloudDatastore |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the job to the $job variable.
2. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Specify the Name parameter value. Save the server to the $cloudServer variable.
3. Run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. Set the $cloudServer variable as the CloudServer parameter value. Specify the Name parameter value. Save the datastore to the $NewCloudDatastore variable.
4. Run the Set-VBRViCloudReplicaJob cmdlet. Set the $job variable as the Job parameter value. Set the $NewCloudDatastore variable as the Datastore parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRCloudServer](get-vbrcloudserver.md)
* [Get-VBRCloudDatastore](get-vbrclouddatastore.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)
* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)
* [Get-VBRLocation](get-vbrlocation.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
