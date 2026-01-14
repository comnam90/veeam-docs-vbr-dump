---
title: "Start-VBRViInstantRecoveryMigration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrviinstantrecoverymigration.html"
last_updated: "8/19/2024"
product_version: "13.0.1.1071"
---

# Start-VBRViInstantRecoveryMigration

In this article

Short Description

Starts VMs quick migration to specified ESXi host.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRViInstantRecoveryMigration -InstantRecovery <InstantRecovery> [-ToTarget] [-Server <CHost>] [-ResourcePool <CViResourcePoolItem>] [-Datastore <CViDatastoreItem>] [-Folder <CViFolderItem>] [-StoragePolicy <VBRViStoragePolicy>] [-SourceProxy <CViProxy[]>] [-TargetProxy <CViProxy[]>] [-DeleteSourceVmFiles] [-ForceVeeamQM] [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts VMs quick migration to specified ESXi host. You can run this cmdlet after you perform [Instant Recovery](instant_cmdlets.md).

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies a running Instant Recovery session. The cmdlet will start a quick migration of VMs that are recovered during this session. | Accepts the InstantRecovery object. To create this object, run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. | True | 0 | True (ByValue, |
| ToTarget | Defines target server settings.  If you migrate VMware vSphere VMs, provide this parameter and do not specify the target server explicitly with the Server parameter, the cmdlet will migrate VMs to the ESXi host that is specified in the Instant Recovery session. Otherwise, it will mirgate VMs to the original ESXi host. | SwitchParameter | False | Named | False |
| Server | Specifies the target ESXi host. The cmdlet will migrate restored VMs to this host.  Note: Consider the following:   * You must not specify a vCenter Server in this parameter. * This parameter is required if you migrate a workload other than a VMware vSphere VM. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ResourcePool | Specifies the resource pool. The cmdlet will migrate restored VMs to this resource pool.  Note: This parameter is required if you migrate a workload other than a VMware vSphere VM. | Accepts the CViResourcePoolItem object. To create this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | False |
| Datastore | Specifies the datastore to which you want to migrate restored VMs. Veeam Backup & Replication will redirect the redo logs to the selected datastore.  Note: This parameter is required if you migrate a workload other than a VMware vSphere VM. | Accepts the CViDatastoreItem object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| Folder | Specifies the folder where you want to store the migrated VM.  Note: This parameter is required if you migrate a workload other than a VMware vSphere VM. | Accepts the CViFolderItem object. To create this object, run the [Find-VBRViFolder](find-vbrvifolder.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy profile that must be applied to the restored virtual disks. | Accepts the VBRViStoragePolicy object. To create this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies an array of the source backup proxies that you want to use as source backup proxies. | Accepts the CViProxy[] object. To create this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies an array of the target backup proxies that you want to use as target backup proxies. | Accepts the CViProxy[] object. To create this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| DeleteSourceVmFiles | Defines that the cmdlet will delete the original VM on the source host after the heartbeat is received.  If you do not provide this parameter, the source VM will not be deleted. All jobs to which the VM is added will continue to process the source VM.  Note: You can not apply this option if you provide the ForceVeeamQM parameter. | SwitchParameter | False | Named | False |
| ForceVeeamQM | Defines that the cmdlet will apply the Veeam Quick Migration mechanism to migrate VMs. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform VM restore even if the geographic location of the repository where VM backups reside and the target host location does not match. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupSession object that contains setting of a VMs quick migration session.

Examples

Performing VMs Quick Migration

This example shows how to migrate the VMs to a the support.north.local ESXi host with the following settings:

* The target resource pool is set to ResourcePool\_9.
* The target datastore is set to Datastore\_5.
* The target folder is set to VM\_recovery.
* The cmdlet will apply the Veeam Quick Migration mechanism to migrate VMs.
* The RunAsync parameter is set to bring the process to the background.

|  |
| --- |
| $session = Get-VBRInstantRecovery  $server = Get-VBRServer -Name support.north.local  $pool = Find-VBRViResourcePool -Name "ResourcePool\_9"  $store = Find-VBRViDatastore -Name "Datastore\_5"  $folder = Find-VBRViFolder -Name "VM\_recovery"  Start-VBRViInstantRecoveryMigration -InstantRecovery $session -Server $server -ResourcePool $pool -Datastore $store -Folder $folder -ForceVeeamQM -RunAsync |

Perform the following steps:

1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. Save the result to the $session variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Provide the Name parameter value. Save the result to the $server variable.
3. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Provide the Name parameter value. Save the result to the $pool variable.
4. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Provide the Name parameter value. Save the result to the $store variable.
5. Run the [Find-VBRViFolder](find-vbrvifolder.md) cmdlet. Provide the Name parameter value. Save the result to the $folder variable.
6. Run the Start-VBRViInstantRecoveryMigration cmdlet. Specify the following settings:

* Set the $session variable as the InstantRecovery parameter value.
* Set the $server variable as the Server parameter value.
* Set the $pool variable as the ResourcePool parameter value.
* Set the $store variable as the Datastore parameter value.
* Set the $folder variable as the Folder parameter value.
* Provide the ForceVeeamQM parameter.
* Provide the RunAsync parameter.

Related Commands

* [Get-VBRInstantRecovery](get-vbrinstantrecovery.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViFolder](find-vbrvifolder.md)

Page updated 8/19/2024

Page content applies to build 13.0.1.1071
