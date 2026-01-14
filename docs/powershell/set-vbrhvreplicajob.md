---
title: "Set-VBRHvReplicaJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvreplicajob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvReplicaJob

In this article

Short Description

Modifies Hyper-V replication jobs.

Applies to

Platform: Hyper-V

For VMware, run the [Set-VBRViReplicaJob](set-vbrvireplicajob.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvReplicaJob -Job <CBackupJob> [-Name <string>] [-Server <CHost>] [-Path <string>] [-Entity <IHvItem[]>] [-Suffix <string>] [-Description <string>] [-SourceRepository <CBackupRepository[]>] [-BackupRepository <CBackupRepository>] [-EnableReIp] [-ReIpRule <IHvReIpRule[]>] [-EnableSeeding] [-RepositorySeed <CBackupRepository>] [-EnableVMMapping] [-OriginalVM <CHvVmItem[]>] [-ReplicaVM <CHvVmItem[]>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an existing Hyper-V replication job.

|  |
| --- |
| Note |
| Consider the following:   * The cmdlet will not run if the geographic location of the VMs added to the job and the job target repository location do not match. If you still want to run the cmdlet, use the Force parameter. * To modify settings, specify new values for the necessary parameters, After you run this cmdlet, the previous settings will be rewritten with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the replication job you want to modify. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Name | True (ByValue, |
| Name | Specifies the name you want to assign to the replication job. | String | False | Named | False |
| Server | Specifies the Hyper-V host where the created replica will be stored. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Path | Specifies the Hyper-V volume where the created replica will be stored. | String | False | Named | False |
| Entity | Specifies the array of VMs you want to add to this job. | Accepts the IHvItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Suffix | Specifies the suffix that will be appended to the name of the VM you are replicating. This name will be used to register the replicated VM on the target server.  Default: "\_replica". | String | False | Named | False |
| Description | Specifies the description of the replication job. | String | False | Named | False |
| SourceRepository | For building replica from backup files.  Specifies the backup repository that will be used to read the VM data from the already existing backup chain.  You cannot specify cloud repository. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the backup repository that will be used to store replica metadata files.  Default: default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableReIp | Enables the option to use the re-IP rules. Use the ReIpRule parameter to set the re-IP rules. | Accepts the [VBRHvReplicaReIpRule](vbrhvreplicareiprule.md) object. To get this object, run the [Get-VBRHvReplicaReIpRule](get-vbrhvreplicareiprule.md) cmdlet. | False | Named | False |
| ReIpRule | Specifies the re-IP rules. | Accepts the [VBRHvReplicaReIpRule](vbrhvreplicareiprule.md) or [VBRHvReplicaReIpIPv6Rule](vbrhvreplicareipipv6rule.md) object. To get this object, run the [Get-VBRHvReplicaReIpRule](get-vbrhvreplicareiprule.md) cmdlet. | False | Named | False |
| EnableSeeding | Enables the option to use seeding for this replication job. | SwitchParameter | False | Named | False |
| RepositorySeed | For replica seeding.  Specifies the backup repository where the seed (the full backup) resides. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableVMMapping | Enables the option to use replica mapping for this replication job. | SwitchParameter | False | Named | False |
| OriginalVM | For replica mapping.  Specifies the production VM you want to replicate using replica mapping.  The replication job will map this VM to a selected replica VM on the DR site.  Use the ReplicaVM parameter to specify the replica VM on the DR site. | Accepts the CHvVmItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | False |
| ReplicaVM | For replica mapping.  Specifies the VM on the DR site you want to use as the replication target. The replication job will map the production VM to this VM.  Use the OriginalVM parameter to specify the production VM. | Accepts the CHvVmItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | False |
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
| This example shows how to configure a re-IP rule for a replication job.  |  | | --- | | $job = Get-VBRJob -Name "Hawk Replication"  $reiprule = New-VBRHvReplicaReIpRule -SourceIp 172.16.\*.\* -SourceMask 255.255.0.0 -TargetIp 172.17.\*.\* -TargetMask 255.255.0.0 -TargetGateway 172.17.0.1  Set-VBRHvReplicaJob -Job $job -EnableReIp -ReIpRule $reiprule |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save it to the $job variable. 2. Run the [New-VBRHvReplicaReIpRule](new-vbrhvreplicareiprule.md) cmdlet. Specify the SourceIp, SourceMask, TargetIp, TargetMask, TargetGateway parameter value. Save it to the $reiprule variable. 3. Run the Set-VBRHvReplicaJob cmdlet. Set the $job variable as the Job parameter value. Provide the EnableReIp parameter. Set the $reiprule variable as the ReIpRule parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Configuring Seeding for Replication Job

|  |  |
| --- | --- |
| This example shows how to configure seeding for a replication job.  |  | | --- | | $job = Get-VBRJob -Name "Hawk Replication"  $repository = Get-VBRBackupRepository -Name "Backup Volume 01"  Set-VBRHvReplicaJob -Job $job -EnableSeeding -RepositorySeed $repository |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save it to the $job variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 3. Run the Set-VBRHvReplicaJob cmdlet. Set the $job variable as the Job parameter value. Provide the EnableSeeding parameter. Set the $repository variable as the RepositorySeed parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Configuring VM Mapping for Replication Job

|  |  |
| --- | --- |
| This example shows how to configure VM mapping for a replication job.  |  | | --- | | $job = Get-VBRJob -Name "Hawk Replication"  $originalvm = Find-VBRHvEntity -Server "Production Host" -Name "Original VM"  $replicavm = Find-VBRHvEntity -Server "DR Host" -Name "Replica VM"  Set-VBRHvReplicaJob -Job $job -EnableVMMapping -OriginalVM $originalvm -ReplicaVM $replicavm |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save it to the $job variable. 2. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Server and Name parameter values. Save it to the $originalvm variable. 3. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Server and Name  parameter values. Save it to the $replicavm variable. 4. Run the Set-VBRHvReplicaJob cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Provide the EnableVMMapping parameter. * Set the $originalvm variable as the OriginalVM parameter value. * Set the $replicavm variable as the ReplicaVM parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRHvEntity](find-vbrhventity.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRHvReplicaReIpRule](new-vbrhvreplicareiprule.md)
* [Get-VBRReplica](get-vbrreplica.md)
* [Get-VBRLocation](get-vbrlocation.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
