---
title: "Start-VBRViComputerInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvicomputerinstantrecovery.html"
last_updated: "12/6/2024"
product_version: "13.0.1.1071"
---

# Start-VBRViComputerInstantRecovery


Short Description

Starts instant recovery of machines to the VMware infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRViComputerInstantRecovery -RestorePoint <COib> -Server <CHost> [-RestoredVMName <string>] [-VMFolder <CViFolderItem>] [-ResourcePool <CViResourcePoolItem>] [-SourceNetwork <VBRComputerNetworkInfo[]>] [-TargetNetwork <IVBRServerNetworkInfo[]>] [-GenerateNewSystemUUID] [-CacheDatastore <VBRViDatastore>] [-StoragePolicy <VBRViStoragePolicy>] [-PowerOnAfterRestoring] [-ConnectVMToNetwork] [-Reason <string>] [-Credentials <CCredentials>] [-RunAsync] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction> {DisableNetwork | AbortRecovery}] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts an instant recovery of machines to the VMware infrastructure. You can restore the following types of machines:

* Microsoft Windows computers backed up by the Veeam Agent.
* Linux computers backed up by the Veeam Agent.
* Hyper-V workloads to restore them to VMware vSphere VMs.

Run the [Start-VBRHvInstantRecovery](start-vbrhvinstantrecovery.md) cmdlet to restore Hyper-V workloads to Hyper-V VMs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of a machine. The cmdlet will use the specified restore point to recover a machine. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Server | For restore to another location.  Specifies the target ESXi host. The cmdlet will restore a machine to this ESXi host.  Note: You must not specify a vCenter Server in this parameter. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| VMFolder | For restore to another location.  Specifies a folder on the ESXi host. The cmdlet will restore a machine to this folder. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViFolder](find-vbrvifolder.md) cmdlet. | False | Named | False |
| RestoredVMName | Specifies a name of the restored machine. The cmdlet will restore the machine with this name.  Note: The VM name must not contain space characters.  Default: The original machine name. | String | False | Named | False |
| ResourcePool | For restore to another location.  Specifies a resource pool on the ESXi host. The cmdlet will restore a machine to this resource pool. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | False |
| SourceNetwork | For restore to another location.  Specifies the source site network. Veeam Backup & Replication will map it to the target network. | Accepts the VBRComputerNetworkInfo[] object. To get this object, run the [Get-VBRComputerNetworkInfo](get-vbrcomputernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For restore to another location.  Specifies the target site network. Veeam Backup & Replication will map it with the source network. | Accepts the IVBRServerNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| GenerateNewSystemUUID | Defines that the cmdlet will generate a new system UUID for the restored machine.  If you do not provide this parameter, the cmdlet will keep the existing system UUID of the restored machine. | SwitchParameter | False | Named | False |
| CacheDatastore | Specifies a datastore to keep redo logs for the restored machine.  Note: If you do not specify this parameter, Veeam Backup & Replication will store redo logs on the vPower NFS server. | Accepts the VBRViDatastore object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy profiles. The cmdlet will restore the specified VMware storage policy associated with the restored Veeam Agent computer.  Note: Veeam Backup & Replication restores the storage policy only if you restore the Veeam Agent computer to the original location. | Accepts the VBRViStoragePolicy object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| PowerOnAfterRestoring | Defines that the cmdlet will power on the restored machine.  If you do not provide this parameter, you will need to power up a restored machine manually. | SwitchParameter | False | Named | False |
| ConnectVMToNetwork | Defines that the cmdlet will restore a machine with initial network settings. | SwitchParameter | False | Named | False |
| Reason | Specifies a reason for performing instant recovery of a machine. | String | False | Named | False |
| Credentials | Used to access the backups of a machine that is stored on shared folders.  Specifies the credentials you want to use to authenticate with the shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| EnableAntivirusScan | Enables the option to perform the secure restore. Veeam Backup & Replication will trigger the antivirus software to scan the selected machine before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For the secure restore option.  Defines that the antivirus will continue to scan a machine after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies the secure restore action when the infection is detected.   * DisableNetwork: use this option if you want to restore a machine with disabled network adapters (NICs). * AbortRecovery: use this option if you want to cancel the restore session. | VBRVirusDetectionAction | False | Named | False |
| Force | Defines that the cmdlet will perform restore of a machine even if the geographic location of the repository where backups of a machine reside and the target host location does not match. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the InstantRecovery object that contains settings of a session that runs to perform instant recovery of machines to the VMware infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Instant Recovery of Veeam Agent Computer using Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to perform instant recovery of a Veeam Agent computer. The Veeam Agent computer will be restored to the esx07.tech.local host as the WindowsAB\_Restored VM.  |  | | --- | | $backup = Get-VBRBackup -Name "Windows Agent Backup\*"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $srv = Get-VBRServer -Name "esx07.tech.local"  Start-VBRViComputerInstantRecovery -RestorePoint $restorepoint[3] -Server $srv -RestoredVMName "WindowsAB\_Restored" |  Perform the following steps:   1. Get the restore point:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.   Note: To get a list of restore points for a Veeam Agent job, you must provide the asterisks sign for the Name parameter value: Name "AgentJob\*". Otherwise, the Get-VBRRestorePoint cmdlet will not return any restore points for the Veeam Agent job.   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $srv variable. 2. Run the Start-VBRViComputerInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $srv variable as the Server parameter value. * Specify the RestoredVMName parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Instant Recovery of Specific Veeam Agent Computer using Latest Restore Point

|  |  |
| --- | --- |
| This example shows how to perform instant recovery of the WindowsAB Veeam Agent computer. The cmdlet will restore the computer to the esx07.tech.local host as the WindowsAB\_Restored VM.  |  | | --- | | $backup = Get-VBRBackup -Name "Windows Agent Backup\*"  $restorepoint = Get-VBRRestorePoint -Name "WindowsAB" -Backup $Backup | Sort-Object –Property CreationTime –Descending | Select-Object -First 1  $srv = Get-VBRServer -Name "esx07.tech.local"  Start-VBRViComputerInstantRecovery -RestorePoint $restorepoint[3] -Server $srv -RestoredVMName "WindowsAB\_Restored" |  Perform the following steps:   1. Get the restore point:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.   Note: To get a list of restore points for a Veeam Agent job, you must provide the asterisks sign for the Name parameter value: Name "AgentJob\*". Otherwise, the Get-VBRRestorePoint cmdlet will not return any restore points for the Veeam Agent job.   1. Run the Get-VBRRestorePoint cmdlet. Specify the Name parameter value. Set the $backup variable as the Backup parameter value. 2. Pipe the cmdlet output to the Sort-Object cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 3. Pipe the cmdlet output to the Select-Object cmdlet. Set the 1 number as the First parameter value.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $srv variable.  1. Run the Start-VBRViComputerInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $srv variable as the Server parameter value.  * Specify the RestoredVMName parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)

* [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7)
* [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7)


