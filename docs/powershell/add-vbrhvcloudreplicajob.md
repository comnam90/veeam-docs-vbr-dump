---
title: "Add-VBRHvCloudReplicaJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvcloudreplicajob.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRHvCloudReplicaJob

In this article

Short Description

Creates a new Hyper-V cloud replication job.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRHvCloudReplicaJob -Server <VBRCloudServer> -Datastore <VBRCloudDatastore> -Entity <IHvItem[]> [-Name <string>] [-Suffix <string>] [-Description <string>] [-SourceRepository <CBackupRepository[]>] [-BackupRepository <CBackupRepository>] [-EnableNetworkMapping] [-SourceNetwork <VBRHvServerNetworkInfo[]>] [-TargetNetwork <VBRCloudServerNetworkInfo[]>] [-SourceWANAccelerator <CWanAccelerator>] [-SourceProxy <CHvProxy[]>] [-RepositorySeed <CBackupRepository>] [-OriginalVM <CHvVmItem[]>] [-ReplicaVM <COib[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new Hyper-V cloud replication job. Cloud replication creates a VM replica on a cloud host and maintains it in synch with the original VM.

Note that cloud replication does not support replica from backup.

When you create a replication job, you can configure the following additional settings:

* Network mapping: this option allows you to configure network mapping rules if the production site and the cloud host uses separate virtual networks. Use the EnableNetworkMapping parameter to enable the network mapping and the SourceNetwork and the TargetNetwork parameters to select the networks.
* Proxy server: this option allows you to assign a particular proxy server for the data transfer. Use the SourceProxy parameter to set the proxy.
* WAN accelerators: this option allows you to use the built-in WAN accelerators to optimize the data transfer. Note that WAN accelerators must work in pair, so you can use the WAN acceleration only if the cloud provider has a WAN accelerator on the target side. Use the SourceWANAccelerator parameter to set the source WAN accelerator.
* Re-IP rules: this option allows you to configure different IP addressing scheme for the production site and the cloud host. You need to create an object containing the re-IP rules beforehand by running the [New-VBRHvReplicaReIpRule](new-vbrhvreplicareiprule.md) cmdlet. Then pass the created object to the ReIpRule parameter of this cmdlet.

Note that when you create a replica job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to run the job manually.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set schedule for the job and run it automatically.

|  |
| --- |
| ![Add-VBRHvCloudReplicaJob](images/icon_note.webp) Note: |
| The cmdlet will not run if the geographic location of the VMs added to the job and the target cloud host location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the string with the name of the created replication job.  If not set, Veeam Backup & Replication will give the default job name. | String | False | Named | False |
| Entity | Specifies the array of VMs you want to replicate. | Accepts the IHvItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | True | Named | True (ByValue, |
| Server | Specifies the cloud host where the created replica should reside. | Accepts the [VBRCloudServer](vbrcloudserver.md) object. To get this object, run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. | True | Named | False |
| Datastore | Specifies the cloud disk volume to which you want to replicate. | Accepts the [VBRCloudDatastore](vbrclouddatastore.md) object. To get this object, run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. | True | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  If omitted, the replicated VMs will have the '\_replica' suffix by default. | String | False | Named | False |
| SourceRepository | Used for building replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain.  You cannot specify cloud repository. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the backup repository which will be used to store replica metadata files.  If not set, the default backup repository will be used. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Description | Specifies the description of the new job. | String | False | Named | False |
| EnableNetworkMapping | Enables the network mapping option.  Use the SourceNetwork and the TargetNetwork parameters to set the network mapping rules. | SwitchParameter | False | Named | False |
| SourceNetwork | Used to set the source network for the EnableNetworkMapping parameter.  Specifies the production network to which VMs added to the job are connected.  Note: the number of the source and the target networks must be the same. | Accepts the [VBRHvServerNetworkInfo[]](vbrhvservernetworkinfo.md) object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | Used to set the target network for the EnableNetworkMapping parameter.  Specifies the network in the DR site to which VM replicas must be connected.  Note: the number of the source and the target networks must be the same. | Accepts the [VBRCloudServerNetworkInfo[]](vbrcloudservernetworkinfo.md) object. To get this object, run the [Get-VBRCloudServerNetworkInfo](get-vbrcloudservernetworkinfo.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the source proxy that will be used by the job.  Default: Automatic selection. | Accepts the CHvProxy[] object. To get this object, run the [Get-VBRHvProxy](get-vbrhvproxy.md) cmdlet. | False | Named | False |
| SourceWANAccelerator | Specifies the WAN accelerator configured in the source site that will be used for data transfer.  Note: you can set the source WAN accelerator only if the cloud provider has a target WAN accelerator configured. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository on which a backup used as a seed for the replication job resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| OriginalVM | For replica mapping.  Specifies the production VM you want to replicate using replica mapping.  The replication job will map this VM to a selected replica VM on the DR site.  Use the ReplicaVM parameter to specify the replica VM on the DR site. | Accepts the CHvVmItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies the VM on the DR site you want to use as the replication target. The replication job will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the COib[] object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a job even if the geographic location of the VMs added to the job and the target cloud host location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

Creating Hyper-V Cloud Replica Job

This example shows how to create a Hyper-V cloud replica job.

|  |
| --- |
| $vm = Find-VBRHvEntity -Name “application\_server”  $cloudServer = Get-VBRCloudServer -Name 104.45.95.227  $cloudDatastore = Get-VBRCloudDatastore -CloudServer $cloudServer –Name “GHJDatastore”  Add-VBRHvCloudReplicaJob -Name “Hv Cloud Replica Job” -Entity $vm -Server $cloudServer -Datastore $cloudDatastore |

Perform the following steps:

1. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet to get the VM you want to replicate. Specify the Name parameter value. Save the result to the $vm variable.
2. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Specify the Name parameter value. Save the server to the $cloudServer variable.
3. Run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. Set the $cloudServer variable as the CloudServer parameter value. Specify the Name parameter value. Save the datastore to the $cloudDatastore variable.
4. Run the Add-VBRHvCloudReplicaJob cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $vm variable as the Entity parameter value.
* Set the $cloudServer variable as the Server parameter value.
* Set the $cloudDatastore variable as the Datastore parameter value.

Related Commands

* [Get-VBRCloudServer](get-vbrcloudserver.md)
* [Get-VBRCloudDatastore](get-vbrclouddatastore.md)
* [Find-VBRHvEntity](find-vbrhventity.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [Get-VBRCloudServerNetworkInfo](get-vbrcloudservernetworkinfo.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)
* [Get-VBRHvProxy](get-vbrhvproxy.md)
* [Get-VBRLocation](get-vbrlocation.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
