---
title: "Start-VBRQuickMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrquickmigration.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Start-VBRQuickMigration


Short Description

Starts Quick Migration of a virtual machine.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRQuickMigration -Entity <CViVmItem[]> -Server <CHost> [-ResourcePool <CViResourcePoolItem>] [-Datastore <CViDatastoreItem>] [-Folder <CViFolderItem>] [-StoragePolicy <VBRViStoragePolicy>] [-SourceProxy <CViProxy[]>] [-TargetProxy <CViProxy[]>] [-ForceVeeamQM] [-DeleteSorceVmFiles] [-RunAsync] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts Quick Migration for a selected virtual machines.

Quick Migration is a service allowing to promptly migrate a VM between ESXi hosts, datastores or both in any state with minimum disruption to business operations and end user access to services.

|  |
| --- |
| ![Start-VBRQuickMigration](images/icon_note.webp) Note: |
| The cmdlet will not run if the geographic location of the VMs you want to migrate and the destination server location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Entity | Specifies the array of virtual machines you want to migrate. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, |
| Server | Specifies the destination server to where you want to migrate the VMs. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| ResourcePool | Specifies the destination resource pool to where you want to migrate the VMs. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | False |
| Datastore | Specifies the destination datastore to where you want to migrate the VMs. | Accepts the CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| Folder | Specifies the destination folder to where you want to migrate the VMs. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViFolder](find-vbrvifolder.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy profile that must be applied to the virtual disks of the VMs. | Accepts the [VBRViStoragePolicy](vbrvistoragepolicy.md) object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies the array of source proxies.  For best migration performance deploy at least one source backup proxy.  Default: automatic selection (recommended). | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies the array of target proxies.  For best migration performance deploy at least one target backup proxy.  Default: automatic selection (recommended). | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| ForceVeeamQM | Defines that the cmdlet will force using Veeam Quick Migration.  If omitted, migration process will use VMware VMotion given that the migration scenario and VMware licensing allows it. | SwitchParameter | False | Named | False |
| DeleteSorceVmFiles | Defines that the original VM will be deleted upon receiving the heartbeat from the VM on the target host. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will start Quick Migration even if the geographic location of the VMs you want to migrate and the destination server location do not match. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Quick Migration of Selected VM

This command starts Quick Migration of the selected VM with the following settings:

* The source and target proxies are not set enabling the Quick Migration mechanism to select them automatically.
* The ForceVeeamQM parameter is not set enabling the use of VMware VMotion.
* The DeleteSourceVmFiles parameter is set to enable the clear up of the original VM files upon successful migration.
* The RunAsync parameter is not set.

|  |
| --- |
| $vm = Find-VBRViEntity -Name "server01.tech.global"  $server = Get-VBRServer -Type ESXi -Name "esx05.tech.local"  $pool = Find-VBRViResourcePool -Server $server  $datastore = Find-VBRViDatastore -Server $server  $folder = Find-VBRViFolder -Server $server  Start-VBRQuickMigration -Entity $vm -Server $server -ResourcePool $pool -Datastore $datastore -Folder $folder -DeleteSorceVmFiles |

Perform the following steps:

1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the ESXi option for the Type parameter. Specify the Name parameter value. Save the result to the $server variable.
3. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $pool variable.
4. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $datastore variable.
5. Run the [Find-VBRViFolder](find-vbrvifolder.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $folder variable.
6. Run the Start-VBRQuickMigration cmdlet. Specify the following settings:

* Set the $vm variable as the Entity parameter value.
* Set the $server variable as the Server parameter value.
* Set the $pool variable as the ResourcePool parameter value.
* Set the $datastore variable as the Datastore parameter value.
* Set the $folder variable as the Folder parameter value.
* Provide the DeleteSorceVmFiles parameter.

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViFolder](find-vbrvifolder.md)
* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VBRLocation](get-vbrlocation.md)


