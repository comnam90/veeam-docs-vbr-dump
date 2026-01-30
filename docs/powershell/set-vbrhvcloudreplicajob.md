---
title: "Set-VBRHvCloudReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvcloudreplicajob.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRHvCloudReplicaJob


Short Description

Modifies a Hyper-V cloud replication job.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvCloudReplicaJob -Job <CBackupJob> [-Name <string>] [-Datastore <VBRCloudDatastore>] [-Entity <IHvItem[]>] [-Suffix <string>] [-Description <string>] [-SourceRepository <CBackupRepository[]>] [-BackupRepository <CBackupRepository>] [-EnableNetworkMapping] [-SourceNetwork <VBRHvServerNetworkInfo[]>] [-TargetNetwork <VBRCloudServerNetworkInfo[]>] [-UseWANAccelerator] [-SourceWANAccelerator <CWanAccelerator>] [-SourceProxy <CHvProxy[]>] [-EnableSeeding] [-RepositorySeed <CBackupRepository>] [-EnableVMMapping] [-OriginalVM <CHvVmItem[]>] [-ReplicaVM <COib[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an existing Hyper-V cloud replication job. To modify settings, you need to specify new values for the necessary parameters. The parameters that you omit will remain unchanged.

|  |
| --- |
| Note |
| Consider the following:   * The cmdlet will not run if the geographic location of the VMs added to the job and the target cloud host location do not match. If you still want to run the cmdlet, use the Force parameter. * To modify settings, specify new values for the necessary parameters. After you run this cmdlet, the previous settings will be rewritten with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the replication job you want to modify. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the string with the name of the created replication job.  If not set, Veeam Backup & Replication will give the default job name. | String | False | Named | False |
| Entity | Specifies the array of VMs you want to replicate. | Accepts the IHvItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | False |
| Datastore | Specifies the cloud disk volume to which you want to replicate. | Accepts the [VBRCloudDatastore](vbrclouddatastore.md) object. To get this object, run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. | False | Named | False |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  If omitted, the replicated VMs will have the '\_replica' suffix by default. | String | False | Named | False |
| SourceRepository | Used for building replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain.  You cannot specify cloud repository. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the backup repository which will be used to store replica metadata files.  Default: default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Description | Specifies the description of the new job. | String | False | Named | False |
| EnableNetworkMapping | Enables the network mapping option. Use the SourceNetwork and the TargetNetwork parameters to set the network mapping rules. | SwitchParameter | False | Named | False |
| SourceNetwork | Used to set the source network for the EnableNetworkMapping parameter.  Specifies the production network to which VMs added to the job are connected.  Note: the number of the source and the target networks must be the same. | Accepts the [VBRHvServerNetworkInfo[]](vbrhvservernetworkinfo.md) object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | Used to set the target network for the EnableNetworkMapping parameter.  Specifies the network in the DR site to which VM replicas must be connected.  Note: the number of the source and the target networks must be the same. | Accepts the [VBRCloudServerNetworkInfo[]](vbrcloudservernetworkinfo.md) object. To get this object, run the [Get-VBRCloudServerNetworkInfo](get-vbrcloudservernetworkinfo.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the source proxy that will be used by the job.  Default: Automatic selection. | Accepts the CHvProxy[] object. To get this object, run the [Get-VBRHvProxy](get-vbrhvproxy.md) cmdlet. | False | Named | False |
| UseWANAccelerator | Defines that the data must be transferred via WAN accelerators.  Use the SourceWANAccelerator parameter to set the WAN accelerator on the source side. | SwitchParameter | False | Named | False |
| SourceWANAccelerator | Specifies the WAN accelerator configured in the source site that will be used for data transfer.  Note: you can set the source WAN accelerator only if the cloud provider has a target WAN accelerator configured. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| EnableSeeding | Enables replica seeding option for the replication job. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository on which a backup used as a seed for the replication job resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| EnableVMMapping | Enables replica mapping option for the replication job. | SwitchParameter | False | Named | False |
| OriginalVM | For replica mapping.  Specifies the production VM you want to replicate using replica mapping.  The replication job will map this VM to a selected replica VM on the DR site.  Use the ReplicaVM parameter to specify the replica VM on the DR site. | Accepts the CHvVmItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| ReplicaVM | For replica mapping.  Specifies the VM on the DR site you want to use as the replication target. The replication job will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the COib[] object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Force | Defines that the cmdlet will modify the cloud replication job even if the geographic location of the VMs added to the job and the target cloud host location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

Changing Cloud Replica Job Settings

This example shows how to apply custom settings to a cloud replica job.

|  |
| --- |
| $job = Get-VBRJob –Name “Hv Cloud Replica Job”  $vms = Find-VBRHvEntity -Name fileserver\*  $cloudServer = Get-VBRCloudServer -Name 104.45.95.227  $NewCloudDatastore = Get-VBRCloudDatastore -CloudServer $cloudServer –Name “KLMDatastore”  Set-VBRHvCloudReplicaJob –Job $job -Entity $vms –Datastore $NewCloudDatastore |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. Save the result to the $vms variable.
3. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Specify the Name parameter value. Save the server to the $cloudServer variable.
4. Run the [Get-VBRCloudDatastore](get-vbrclouddatastore.md) cmdlet. Set the $cloudServer variable as the CloudServer parameter value. Specify the Name parameter value. Save the datastore to the $NewCloudDatastore variable.
5. Run the Set-VBRHvCloudReplicaJob cmdlet. Specify the following settings:

* Set the $job variable as the Job parameter value.
* Set the $vms variable as the Entity parameter value.
* Set the $NewCloudDatastore variable as the Datastore parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRCloudServer](get-vbrcloudserver.md)
* [Get-VBRCloudDatastore](get-vbrclouddatastore.md)
* [Find-VBRHvEntity](find-vbrhventity.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [Get-VBRCloudServerNetworkInfo](get-vbrcloudservernetworkinfo.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)
* [Get-VBRHvProxy](get-vbrhvproxy.md)
* [Get-VBRLocation](get-vbrlocation.md)


