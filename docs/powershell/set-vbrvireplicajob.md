---
title: "Set-VBRViReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvireplicajob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViReplicaJob


Short Description

Modifies VMware replication jobs.

Applies to

Platform: VMware

For Hyper-V, run the [Set-VBRHvReplicaJob](set-vbrhvreplicajob.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViReplicaJob -Job <CBackupJob> [-Name <string>] [-Server <Object>] [-Entity <IViItem[]>] [-Datastore <VBRViDatastoreBase>] [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Suffix <string>] [-BackupRepository <CBackupRepository>] [-Description <string>] [-EnableNetworkMapping] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>] [-SourceProxy <CViProxy[]>] [-TargetProxy <CViProxy[]>] [-UseWANAccelerator] [-SourceWANAccelerator <CWanAccelerator>] [-TargetWANAccelerator <CWanAccelerator>] [-RestorePointsToKeep <int>] [-ReplicateFromBackup] [-SourceRepository <CBackupRepository[]>] [-EnableReIp] [-ReIpRule <IViReIpRule[]>] [-DiskType <EDiskCreationMode> {Source | Thick | Thin | ThickEagerZeroed}] [-EnableSeeding] [-RepositorySeed <CBackupRepository>] [-EnableVMMapping] [-OriginalVM <CViVmItem[]>] [-ReplicaVM <CViVmItem[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an existing VMware replication job.

|  |
| --- |
| Note |
| Consider the following:   * The cmdlet will not run if the geographic location of the VMs added to the job and the job target repository location do not match. If you still want to run the cmdlet, use the Force parameter. * To modify settings, specify new values for the necessary parameters, After you run this cmdlet, the previous settings will be rewritten with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the replication job you want to modify. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name you want to assign to the replication job. | String | False | Named | False |
| Server | Specifies the target host where the created replica will be stored. | Accepts the CHost or CViClusterItem objects. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Entity | Specifies the array of  VMs you want to add to this job. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Datastore | Specifies the datastore to which you want to replicate. | Accepts the VBRViDatastore or [VBRViDatastoreCluster](vbrvidatastorecluster.md) objects. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| ResourcePool | Specifies the resource pool to which you want to replicate. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | False |
| Folder | Specifies the folder to which you want to replicate. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  Default: "\_replica". | String | False | Named | False |
| BackupRepository | Specifies the backup repository that will be used to store replica metadata files.  Default: Default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Description | Specifies the description of the new job. | String | False | Named | False |
| EnableNetworkMapping | Enables network mapping. Use the SourceNetwork and the TargetNetwork parameters to set the network mapping rules. | SwitchParameter | False | Named | False |
| SourceNetwork | For network mapping.  Specifies the array of production networks to which the VMs in the job are connected.  Note: the number of the source and the target networks must be the same. | Accepts the [VBRViNetworkInfo[]](vbrvinetworkinfo.md) object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For network mapping.  Specifies the array of networks in the DR site. The replicated VMs will be connected to these networks.  Note: the number of the source and the target networks must be the same. | Accepts the [VBRViNetworkInfo[]](vbrvinetworkinfo.md) object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the source proxy you want to assign to the job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies the target proxy you want to assign to the job.  Default: Automatic selection. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| UseWANAccelerator | Defines that the data will be transferred via WAN accelerators.  Use the SourceWANAccelerator and TargetWANAccelerator parameters to set the pair of WAN accelerators. | SwitchParameter | False | Named | False |
| SourceWANAccelerator | Specifies the WAN accelerator configured in the source site that will be used for data transfer.  Remember to set the pair of source and target WAN accelerators.  Default: Not set. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| TargetWANAccelerator | Specifies the WAN accelerator configured in the target site that will be used for data transfer.  Remember to set the pair of source and target WAN accelerators.  Default: Not set. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| RestorePointsToKeep | Specifies the number of restore points you want to keep.  Permitted values: 1 to 28.  Default: 7. | Int32 | False | Named | False |
| ReplicateFromBackup | For building replica from backup files.  If set to $true, the job will use the backups in repository to build the replica. Use the SourceRepository parameter to set the repository. | SwitchParameter | False | Named | False |
| SourceRepository | For building replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableReIp | Enables the option to use the re-IP rules. Use the ReIpRule parameter to set the re-IP rules. | SwitchParameter | False | Named | False |
| ReIpRule | Specifies the re-IP rules. | Accepts the [VBRViReplicaReIpRule](vbrvireplicareiprule.md) or [VBRViReplicaReIpIPv6Rule](vbrvireplicareipipv6rule.md) object. To get this object, run the [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md) cmdlet. | False | Named | False |
| DiskType | Specifies the format that will be used to restore replica disk files:   * Source: the restored replica disks will be the same format as source. * Thick: the restored replica disks will be thick. * Thin: the restored replica disks will be thin.   Default: Source. | EDiskCreationMode | False | Named | False |
| EnableSeeding | Enables the option to use seeding for this replication job. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository where the seed (the full backup) resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| EnableVMMapping | Enables the option to use replica mapping for this replication job. | SwitchParameter | False | Named | False |
| OriginalVM | For replica mapping.  Specifies the production VM you want to replicate using replica mapping.  The replication job will map this VM to a selected replica VM on the DR site.  Use the ReplicaVM parameter to specify the replica VM on the DR site. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| ReplicaVM | For replica mapping.  Specifies the VM on the DR site you want to use as the replication target. The replication job will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Force | Defines that the cmdlet will modify the job even if the geographic location of the VMs added to the job and the target host location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Configuring Re-IP Rule for Replication Job

|  |  |
| --- | --- |
| This example shows how to configure a re-IP rule for a replication job.  |  | | --- | | $job = Get-VBRJob -Name "Apache Replication"  $reiprule = New-VBRViReplicaReIpRule -SourceIp 172.16.\*.\* -SourceMask 255.255.0.0 -TargetIp 172.17.\*.\* -TargetMask 255.255.0.0 -TargetGateway 172.17.0.1  Set-VBRViReplicaJob -Job $job -EnableReIp -ReIpRule $reiprule |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRViReplicaReIpRule](new-vbrvireplicareiprule.md) cmdlet. Specify the SourceIp, SourceMask, TargetIp, TargetMask and TargetGateway parameter values. Save the result to the $reiprule variable. 3. Run the Set-VBRViReplicaJob cmdlet. Set the $job variable as the Job parameter value. Provide the EnableReIp parameter. Set the $reiprule variable as the ReIpRule parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Configuring Seeding for Replication Job

|  |  |
| --- | --- |
| This example shows how to configure seeding for a replication job.  |  | | --- | | $job = Get-VBRJob -Name "Apache Replication"  $repository = Get-VBRBackupRepository -Name "Backup Volume 01"  Set-VBRViReplicaJob -Job $job -EnableSeeding -RepositorySeed $repository |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Set-VBRViReplicaJob cmdlet. Set the $job variable as the Job parameter value. Provide the EnableSeeding parameter. Set the $repository variable as the RepositorySeed parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Configuring VM Mapping for Replication Job

|  |  |
| --- | --- |
| This example shows how to configure VM mapping for a replication job.  |  | | --- | | $job = Get-VBRJob -Name "Apache Replication"  $originalvm = Find-VBRViEntity -Server "Production Host" -Name "Original VM"  $replicavm = Find-VBRViEntity -Server "DR Host" -Name "Replica VM"  Set-VBRViReplicaJob -Job $job -EnableVMMapping -OriginalVM $originalvm -ReplicaVM $replicavm |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $originalvm variable. 3. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $replicavm variable. 4. Run the Set-VBRViReplicaJob cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Provide the EnableVMMapping parameter. * Set the $originalvm variable as the OriginalVM parameter value. * Set the $replicavm variable as the ReplicaVM parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViFolder](find-vbrvifolder.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)
* [New-VBRViReplicaReIpRule](new-vbrvireplicareiprule.md)
* [Get-VBRLocation](get-vbrlocation.md)


