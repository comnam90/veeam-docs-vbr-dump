---
title: "Start-VBRInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrinstantrecovery.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---

# Start-VBRInstantRecovery


Short Description

Starts VMware Instant Recovery.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRInstantRecovery -RestorePoint <COib> -Server <CHost> [-ResourcePool <CViResourcePoolItem>] [-VMName <string>] [-Datastore <CViDatastoreItem>] [-StoragePolicy <VBRViStoragePolicy>] [-Folder <CViFolderItem>] [-PowerUp] [-NICsEnabled] [-Reason <string>] [-Credentials <CCredentials>] [-RunAsync] [-Force] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>] [-EnableTagRestore] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction> {DisableNetwork | AbortRecovery}] [-GenerateNewSystemUUID]  [<CommonParameters>] |

Detailed Description

This cmdlet starts VM instant recovery. With this cmdlet, you can perform the following recover scenarios:

* Restore to original location
* Restore to original location with different settings

* Restore to another location
* Secure restore

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point to which you want to recover the VM. | Accepts the COib object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| VMName | Specifies a name you want to apply to the restored VM. By default, the original VM name is applied. | String | False | Named | False |
| Server | For restore to another location.  Specifies the target ESXi host where you want to locate the restored VM.  Note: You must not specify a vCenter Server in this parameter. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 2 | False |
| ResourcePool | For restore to another location.  Specifies the resource pool where you want to locate the restored VM. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | 3 | False |
| Datastore | For restore to another location.  Specifies the datastore to which you want to store the changes made to the VM during the Instant Recovery. Veeam Backup & Replication will redirect the redo logs to the selected datastore. | Accepts the CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy profile that must be applied to the restored virtual disks. | Accepts the [VBRViStoragePolicy](vbrvistoragepolicy.md) object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| Folder | For restore to another location.  Specifies the folder where you want to locate the restored VM. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| PowerUp | If set to True, the restored VM will be powered up immediately after the restore. Otherwise, you will have to power up the VM manually. | SwitchParameter | False | Named | False |
| NICsEnabled | If set to True, the restored VM will be connected to the network. Otherwise the VM will have no network connections. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing restore of the selected VM.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform VM restore even if the geographic location of the repository where VM backups reside and the target host location does not match. | SwitchParameter | False | Named | False |
| EnableAntivirusScan | Enables the secure restore option. Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Defines that the antivirus will continue VMs scan after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies the secure restore action when the infection is detected.   * DisableNetwork - use this option if you want to restore VMs with disabled network adapters (NICs). * AbortRecovery - use this option if you want to cancel the restore session. | VBRVirusDetectionAction | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the VM. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| EnableTagRestore | Enables the option to restore VMware tags. | SwitchParameter | False | Named | False |
| SourceNetwork | For restore to another location.  Specifies the source site network. Veeam Backup & Replication will map it to the target network. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For restore to another location.  Specifies the target site network. Veeam Backup & Replication will map it with the source network. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| GenerateNewSystemUUID | Defines that the cmdlet will generate a new system UUID for the restored machine.  Note: Currently this parameter supports only the $false value: GenerateNewSystemUUID:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring VM to Original Location and Latest Restore Point

|  |  |
| --- | --- |
| This example shows how to restore a VM to its original location and to the latest restore point.  |  | | --- | | $backup = Get-VBRBackup -Name "Support Backup"  $restorepoint = Get-VBRRestorePoint -Backup $backup | Sort-Object –Property CreationTime –Descending | Select -First 1  $server = Get-VBRServer -Type ESXi -Name esx02.support.local  Start-VBRInstantRecovery -RestorePoint $restorepoint -Server $server |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Get the most recent VM restore point:  * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. * Pipe the cmdlet output to the Sort-Object method to filter restore points by the CreationTime property. * Save the result to the $restorepoint variable.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the ESXi option for the Type parameter. Specify the Name parameter value. Save the result to the $server variable.   If you do not know the name of the source ESXi host, you can get it from the properties of the VM restore point. To do that, run the $restorepoint.AuxData.EsxName command. PowerShell will return the name of the source ESXi host.   1. Run the Start-VBRInstantRecovery cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring VM to Another Location with Different Settings

|  |  |
| --- | --- |
| This example shows how to restore the VM to another location with different settings. The job will run with the following settings:   * The name of the restored VM is MSExchange\_Restored. * The PowerUp parameter is used to enable the auto power up of the restored VM. * The NICsEnabled parameter is used to connect the restored VM to the host network. * The RunAsync parameter is set to bring the process to the background.   |  | | --- | | $restorepoint = Get-VBRRestorePoint  $server = Get-VBRServer -Name support.north.local  $pool = Find-VBRViResourcePool -Name "ResourcePool\_9"  $store = Find-VBRViDatastore -Name "Datastore\_5"  $folder = Find-VBRViFolder -Name "VM\_recovery"  Start-VBRInstantRecovery -RestorePoint $restorepoint -VMName "MSExchange\_Restored" -Server $server -ResourcePool $pool -Datastore $store -Folder $folder -PowerUp:$true -NICsEnabled:$true -Reason "Data recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Specify the Name parameter value. Save the result to the $pool variable. 4. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Name parameter value. Save the result to the $store variable. 5. Run the [Find-VBRViFolder](find-vbrvifolder.md) cmdlet. Specify the Name parameter value. Save the result to the $folder variable. 6. Run the Start-VBRInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the VMName parameter value. * Set the $server variable as the Server parameter value. * Set the $pool variable as the ResourcePool parameter value. * Set the $store variable as the Datastore parameter value. * Set the $folder variable as the Folder parameter value. * Provide the PowerUp and NICsEnabled parameters. * Specify the Reason parameter value. * Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Secure VM Restore

|  |  |
| --- | --- |
| The example shows how to perform secure restore of the selected VM. The restore session will run with the following settings:   * The antivirus will continue VM scan after the first virus threat is found. * In case the threat is detected, Veeam Backup & Replication will cancel the restore session. * The RunAsync parameter is set to bring the process to the background.   |  | | --- | | $restorepoint = Get-VBRRestorePoint  Start-VBRInstantRecovery -RestorePoint $restorepoint[1] -RunAsync -EnableAntivirusScan -EnableEntireVolumeScan -VirusDetectionAction AbortRecovery |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the second restore point is used.   * Provide the RunAsync parameter. * Provide the EnableAntivirusScan parameter.  * Provide the EnableEntireVolumeScan parameter.  * Set the AbortRecovery option for the VirusDetectionAction parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViFolder](find-vbrvifolder.md)
* [Get-VBRLocation](get-vbrlocation.md)


