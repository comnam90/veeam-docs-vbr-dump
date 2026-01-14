---
title: "Add-VBRHvReplicaJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvreplicajob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRHvReplicaJob

In this article

Short Description

Creates Hyper-V replication jobs.

Applies to

Platform: Hyper-V

For VMware, run the [Add-VBRViReplicaJob](add-vbrvireplicajob.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRHvReplicaJob -Server <CHost> -Entity <IHvItem[]> [-Name <string>] [-Path <string>] [-Suffix <string>] [-Description <string>] [-SourceRepository <CBackupRepository[]>] [-BackupRepository <CBackupRepository>] [-ReIpRule <IHvReIpRule[]>] [-RepositorySeed <CBackupRepository>] [-OriginalVM <CHvVmItem[]>] [-ReplicaVM <CHvVmItem[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new Hyper-V replication job.

You can select a data source from which VM data must be read:

* Actual VM: Veeam Backup & Replication will copy an actual VM from production storage. The created replica will mirror an actual VM state.

Use the Entity parameter to indicate the VMs you want to replicate.

* Replica from backup files:  Veeam Backup & Replication will build a replica from backup files stored in a backup repository. The created replica will be in the latest state the VM is available in backups.

Use the Entity parameter to indicate the VMs you want to replicate and the BackupRepository parameter to set the repository from where the backup files must be read.

Note that when you create a replica job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the created job manually.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set schedule for the job and run it automatically.

|  |
| --- |
| Note |
| The cmdlet will not run if the geographic location of the VMs added to the job and the job target repository location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the replication job. | String | False | Named | False |
| Server | Specifies the target Hyper-V host where the created replica will be stored. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Path | Specifies the Hyper-V volume where the created replica will be stored. | String | False | Named | False |
| Entity | Specifies the array of VMs you want to add to this job. | Accepts the IHvItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | True | Named | True (ByValue, |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  Default: "\_replica". | String | False | Named | False |
| Description | Specifies the description of the replication job. | String | False | Named | False |
| SourceRepository | For building replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain.  You cannot specify cloud repository. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the backup repository that will be used to store replica metadata files.  Default: default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| ReIpRule | Specifies the re-IP rules. | Accepts the [VBRHvReplicaReIpRule](vbrhvreplicareiprule.md) or [VBRHvReplicaReIpIPv6Rule](vbrhvreplicareipipv6rule.md) object. To get this object, run the [Get-VBRHvReplicaReIpRule](get-vbrhvreplicareiprule.md) cmdlet. | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository where the seed (the full backup) resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| OriginalVM | For replica mapping.  Specifies the production VM you want to replicate using replica mapping.  The replication job will map this VM to a selected replica VM on the DR site.  Use the ReplicaVM parameter to specify the replica VM on the DR site. | Accepts the CHvVmItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies the VM on the DR site you want to use as the replication target. The replication job will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the CHvVmItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a job even if the geographic location of the VMs added to the job and the target host location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating VM Replica from Production Storage

|  |  |
| --- | --- |
| This example shows how to create a VM replica from a production storage.  |  | | --- | | $entity = Find-VBRHvEntity -Name "sql02"  $targetserver = Get-VBRServer -Type HvServer -Name "Hv\_Server"  Add-VBRHvReplicaJob -Name "SQL02 Replica job" -Entity $entity -Server $targetserver -Path "c:\Replicas" -Suffix "\_replicated" -Description "SQL02 replication" |  Perform the following steps:   1. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. Save the result to the $entity variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the HvServer value as the Type parameter value. Specify the Name parameter value. Save it to the $targetserver variable. 3. Run the Add-VBRHvReplicaJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $entity variable as the Entity parameter value. * Set the $targetserver variable as the Server parameter value. * Specify the Path parameter value. * Specify the Suffix parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating VM Replica from Backup Files

|  |  |
| --- | --- |
| This example shows how to create a VM replica from backup files.  |  | | --- | | $sql02 = Find-VBRHvEntity -Name "HvExchange"  $targetserver = Get-VBRServer -Type HvServer -Name "Hv\_Server"  $repository = Get-VBRBackupRepository -Name "Backups Vol2"  Add-VBRHvReplicaJob -Name "SQL02 Replica job" -Server $targetserver -Path "c:\Replicas" -Entity $sql02 -Description "SQL02 replication" -SourceRepository $repository |  Perform the following steps:   1. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. Save the result to the $sql02 variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the HvServer value as the Type parameter value. Specify the Name parameter value. Save it to the $targetserver variable. 3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 4. Run the Add-VBRHvReplicaJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $targetserver variable as the Server parameter value. * Specify the Path parameter value. * Set the $sql02 variable as the Entity parameter value. * Specify the Description parameter value. * Set the $repository variable as the SourceRepository parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRHvEntity](find-vbrhventity.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRLocation](get-vbrlocation.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
