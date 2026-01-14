---
title: "Add-VBRViCloudReplicaJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvicloudreplicajob.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRViCloudReplicaJob

In this article

Short Description

Creates a new VMware cloud replication job.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViCloudReplicaJob -Entity <IViItem[]> -Server <VBRCloudServer> -Datastore <VBRCloudDatastore> [-Name <string>] [-Description <string>] [-Suffix <string>] [-BackupRepository <CBackupRepository>] [-SourceRepository <CBackupRepository[]>] [-EnableNetworkMapping] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRCloudServerNetworkInfo[]>] [-SourceProxy <CViProxy[]>] [-SourceWANAccelerator <CWanAccelerator>] [-DiskType <EDiskCreationMode> {Source | Thick | Thin | ThickEagerZeroed}] [-RepositorySeed <CBackupRepository>] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <COib[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new VMware cloud replication job. Cloud replication creates a VM replica on a cloud host and maintains it in sync with the original VM.

Note that cloud replication does not support replica from backup.

When you create a replication job, you can configure the following additional settings:

* Network mapping: this option allows you to configure network mapping rules if the production site and the cloud host uses separate virtual networks. Use the EnableNetworkMapping parameter to enable the network mapping and the SourceNetwork and the TargetNetwork parameters to select the networks.
* Proxy server: this option allows you to assign particular proxy server for the data transfer. Use the SourceProxy parameter to set the proxy explicitly or leave the default (Automatic selection).
* WAN accelerators: this option allows you to use the built-in WAN accelerators to optimize the data transfer. Note that WAN accelerators must work in pair, so you can use the WAN acceleration only if the cloud provider has a WAN accelerator on the target side. Use the SourceWANAccelerator parameter to set the source WAN accelerator.
* Re-IP rules: this option allows you to configure different IP addressing scheme for the production site and the cloud host. You need to create an object containing the re-IP rules beforehand by running the [New-VBRViReplicaReIpRule](new-vbrvireplicareiprule.md) cmdlet. Then pass the created object to the ReIpRule parameter of this cmdlet.

Note that when you create a replica job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to run the job manually.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set schedule for the job and run it automatically.

|  |
| --- |
| Note |
| The cmdlet will not run if the geographic location of the VMs added to the job and the target cloud host location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Entity | Specifies the array of VMs you want to add to the job. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, |
| Server | Specifies the cloud host allocated by the service provider through the hardware plan. The replicas will be created on this host. | Accepts the [VBRCloudServer](vbrcloudserver.md) object. To get this object, run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. | True | Named | False |
| Datastore | Specifies the cloud datastore to which you want to replicate. | Accepts the [VBRCloudDatastore](vbrclouddatastore.md) object. To get this object, run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. | True | Named | False |
| Name | Specifies the name you want to assign to the cloud replication job. | String | False | Named | False |
| Description | Specifies the description of the new job. | String | False | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  Note: If you omit this parameter, the replicated VMs will get the '\_replica' suffix. | String | False | Named | False |
| BackupRepository | Specifies the user backup repository that will be used to store replica metadata files.  If not set, the default backup repository will be used. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| SourceRepository | Used for building replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain.  You cannot specify cloud repository. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableNetworkMapping | Enables the network mapping option. Use the SourceNetwork and the TargetNetwork parameters to set the network mapping rules. | SwitchParameter | False | Named | False |
| SourceNetwork | Used to set the source network for the EnableNetworkMapping parameter.  Specifies the production network to which VMs added to the job are connected.  Note: The number of the source and the target networks must be the same. | Accepts the [VBRViNetworkInfo[]](vbrvinetworkinfo.md) object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | Used to set the target network for the EnableNetworkMapping parameter.  Specifies the network in the DR site to which VM replicas must be connected.  Note: The number of the source and the target networks must be the same. | Accepts the [VBRCloudServerNetworkInfo[]](vbrcloudservernetworkinfo.md) object. To get this object, run the [Get-VBRCloudServerNetworkInfo](get-vbrcloudservernetworkinfo.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the source proxy that will be used by the job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| SourceWANAccelerator | Specifies the WAN accelerator configured in the source site that will be used for data transfer.  Note: you can set the source WAN accelerator only if the cloud provider has a target WAN accelerator configured. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| DiskType | Specifies the format that will be used to restore replica disk files:   * Source: the restored replica disks will be the same format as source. * Thick: the restored replica disks will be thick. * Thin: the restored replica disks will be thick.   Default: Source. | EDiskCreationMode | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository where the seed (the full backup) resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| OriginalVM | For replica mapping.  Specifies the production VM you want to replicate using replica mapping.  The replication job will map this VM to a selected replica VM on the DR site.  Use the ReplicaVM parameter to specify the replica VM on the DR site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies the VM on the DR site you want to use as the replication target. The replication job will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the COib[] object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a job even if the geographic location of the VMs added to the job and the target cloud host location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

Creating Cloud Replica Job

This example shows how to create a cloud replica job.

|  |
| --- |
| $vm = Find-VBRViEntity -Name “web\_application\_server”  $cloudServer = Get-VBRCloudServer -Name 104.45.95.227  $cloudDatastore = Get-VBRCloudDatastore -CloudServer $cloudServer –Name “ABCDatastore”  Add-VBRViCloudReplicaJob -Name “Cloud Replica Job” -Entity $vm -Server $cloudServer -Datastore $cloudDatastore |

Perform the following steps:

1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable.
2. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudServer variable.
3. Run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. Set the $cloudServer variable as the CloudServer parameter value. Specify the Name parameter value. Save the datastore to the $cloudDatastore variable.
4. Run the Add-VBRViCloudReplicaJob cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $vm variable as the Entity parameter value.
* Set the $cloudServer variable as the Server parameter value.
* Set the $cloudDatastore variable as the Datastore parameter value.

Related Commands

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
