---
title: "Add-VBRViReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvireplicajob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRViReplicaJob


Short Description

Creates VMware replication jobs.

Applies to

Platform: VMware

For Hyper-V, run the [Add-VBRHvReplicaJob](add-vbrhvreplicajob.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViReplicaJob -Server <Object> -Entity <IViItem[]> [-Name <string>] [-Datastore <VBRViDatastoreBase>] [-StoragePolicy <VBRViStoragePolicy>] [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Suffix <string>] [-BackupRepository <CBackupRepository>] [-Description <string>] [-EnableNetworkMapping] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>] [-SourceProxy <CViProxy[]>] [-TargetProxy <CViProxy[]>] [-SourceWANAccelerator <CWanAccelerator>] [-TargetWANAccelerator <CWanAccelerator>] [-RestorePointsToKeep <int>] [-SourceRepository <CBackupRepository[]>] [-ReIpRule <IViReIpRule[]>] [-DiskType <EDiskCreationMode> {Source | Thick | Thin | ThickEagerZeroed}] [-RepositorySeed <CBackupRepository>] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <CViVmItem[]>] [-Force] [-HighPriority] [-Multitag]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new VMware replication job.

You can select a data source from which VM data must be read:

* Actual VM: Veeam Backup & Replication will copy an actual VM from production storage. The created replica will mirror an actual VM state.

Use the Entity parameter to indicate the VMs you want to replicate.

* Replica from backup files: Veeam Backup & Replication will build a replica from backup files stored in a backup repository. The created replica will be in the latest state the VM is available in backups.

Use the Entity parameter to indicate the VMs you want to replicate and the SourceRepository parameter to set the repository from where the backup files must be read.

When you create a replication job, you can configure the following additional settings:

* Storage policy profile: you can apply a particular VMware storage policy profile to virtual disks of the replica VM. Use the StoragePolicy parameter to set the profile.
* Network mapping: this option allows you to configure network mapping rules if the production site and DR site use separate virtual networks. Use the EnableNetworkMapping parameter to enable the network mapping and the SourceNetwork and the TargetNetwork parameters to select the networks.
* Proxy servers: this option allows you to configure particular proxy servers for the data transfer. Use the SourceProxy and the TargetProxy parameters to set the proxies.
* WAN accelerators: this option allows you to use the built-in WAN accelerators to optimize the data transfer. Use the SourceWANAccelerator and the TargetWANAccelerator parameters to set the WAN accelerators. Note that WAN acceleration is available only in the Enterprise Plus, Veeam Universal License edition.
* Re-IP rules: this option allows you to configure different IP addressing scheme for the production and the DR sites. You need to create an object containing the re-IP rules beforehand by running the [New-VBRViReplicaReIpRule](new-vbrvireplicareiprule.md) or [New-VBRViReplicaReIpIPv6Rule](new-vbrvireplicareipipv6rule.md) cmdlet. Pass the created object to the ReIpRule parameter of this cmdlet.

Note that when you create a replica job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to run the job manually.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set the schedule for the job and run it automatically.

|  |
| --- |
| Note |
| The cmdlet will not run if the geographic location of the VMs added to the job and the job target repository location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the replication job. | String | False | Named | False |
| Server | Specifies the target VMware host where the created replica will be stored. | Accepts the CHost or CViClusterItem objects. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Entity | Specifies the array of VMs you want to add to this job. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, |
| Datastore | Specifies the datastore to which you want to replicate. | Accepts the VBRViDatastore or [VBRViDatastoreCluster](vbrvidatastorecluster.md) objects. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy profile that must be applied to the replica virtual disks. | Accepts the [VBRViStoragePolicy](vbrvistoragepolicy.md) object.  To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| ResourcePool | Specifies the resource pool to which you want to replicate. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | False |
| Folder | Specifies the folder to which you want to replicate. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  Default: "\_replica". | String | False | Named | False |
| BackupRepository | Specifies the backup repository that will be used to store replica metadata files.  Default: default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Description | Specifies the description of the new job. | String | False | Named | False |
| EnableNetworkMapping | Enables network mapping. Use the SourceNetwork and the TargetNetwork parameters to set the network mapping rules. | SwitchParameter | False | Named | False |
| SourceNetwork | For network mapping.  Specifies the array of production networks to which the VMs in the job are connected.  Note: The number of the source and the target networks must be the same. | Accepts the [VBRViNetworkInfo[]](vbrvinetworkinfo.md) object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For network mapping.  Specifies the array of networks in the disaster recovery site. The replicated VMs will be connected to these networks.  Note: The number of the source and the target networks must be the same. | Accepts the [VBRViNetworkInfo[]](vbrvinetworkinfo.md) object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the source proxy that you want to assign to the job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies the target proxy that you want to assign to the job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| SourceWANAccelerator | Specifies the WAN accelerator configured in the source site that will be used for data transfer.  Remember to set the pair of source and target WAN accelerators.  Default: Not set. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| TargetWANAccelerator | Specifies the WAN accelerator configured in the target site that will be used for data transfer.  Remember to set the pair of source and target WAN accelerators.  Default: Not set. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| RestorePointsToKeep | Specifies the number of restore points you want to keep.  Permitted values: 1 to 28.  Default: 7. | Int32 | False | Named | False |
| SourceRepository | For building replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| ReIpRule | Specifies the re-IP rules. | Accepts the [VBRViReplicaReIpRule](vbrvireplicareiprule.md) or [VBRViReplicaReIpIPv6Rule](vbrvireplicareipipv6rule.md) object. To get this object, run the [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md) cmdlet. | False | Named | False |
| DiskType | Specifies the format that will be used to restore replica disk files:   * Source: the restored replica disks will be the same format as source. * Thick: the restored replica disks will be thick. * Thin: the restored replica disks will be thin.   Default: Source. | EDiskCreationMode | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository where the seed (the full backup) resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| OriginalVM | For replica mapping.  Specifies a production VM you want to replicate using replica mapping.  The replication job will map this VM to a selected replica VM on the disaster recovery site.  Use the ReplicaVM parameter to specify the replica VM on the disaster recovery site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies a VM on the disaster recovery site. The cmdlet will map the production VM to this VM, and the replication job will replicate data to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a job even if the geographic location of the VMs added to the job and the target host location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |
| Multitag | Defines that the cmdlet will replicate tags. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

Creating Replication Job

This example shows how to create a replication job.

|  |
| --- |
| $server = Get-VBRServer -Name "DR Host"  $vm = Find-VBRViEntity -Server $server -Name "DC"  $pool = Find-VBRViResourcePool -Server "DR Host" -Name "ResourcePool\_05"  $datastore = Find-VBRViDatastore -Server "DR Host" -Name "LocalStore"  Add-VBRViReplicaJob -Name "DC Replication Job" -Server $server -Entity $vm -ResourcePool $pool -Datastore $datastore -Suffix "\_replicated" |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $vm variable.
3. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $pool variable.
4. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $datastore variable.
5. Run the Add-VBRViReplicaJob cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $server variable as the Server parameter value.
* Set the $vm variable as the Entity parameter value.
* Set the $pool variable as the ResourcePool parameter value.
* Set the $datastore variable as the Datastore parameter value.
* Specify the Suffix parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViFolder](find-vbrvifolder.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)
* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)
* [New-VBRViReplicaReIpRule](new-vbrvireplicareiprule.md)
* [Get-VBRLocation](get-vbrlocation.md)


