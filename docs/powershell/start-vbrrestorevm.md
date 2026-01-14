---
title: "Start-VBRRestoreVM"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrrestorevm.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---

# Start-VBRRestoreVM

In this article

Short Description

Starts restore of the entire VMware VM.

Applies to

Platform: VMware

For Hyper-V, run the [Start-VBRHvRestoreVM](start-vbrhvrestorevm.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore to another location.

|  |
| --- |
| Start-VBRRestoreVM -RestorePoint <COib> -Server <CHost> [-ResourcePool <CViResourcePoolItem>] [-Datastore <CViDatastoreItem>] [-Folder <CViFolderItem>] [-StoragePolicy <VBRViStoragePolicy>] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>] [-VMName <string>] [-DiskType <EDiskCreationMode> {Source | Thick | Thin | ThickEagerZeroed}] [-PowerUp <bool>] [-SkipTagsRestore] [-Reason <string>] [-RunAsync] [-Credentials <CCredentials>] [-Force] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction> {DisableNetwork | AbortRecovery}] [-NICsEnabled] [-Proxy <CViProxy[]>]  [<CommonParameters>] |

* Restore to a new location, or to original location with different settings.

|  |
| --- |
| Start-VBRRestoreVM -RestorePoint <COib> -Server <CHost> [-ResourcePool <CViResourcePoolItem>] [-Datastore <CViDatastoreItem>] -EnableStagedRestore -StagingVirtualLab <CViSbVirtualLab> -StagingScript <string> -StagingCredentials <CInternalCredentials> [-Folder <CViFolderItem>] [-StoragePolicy <VBRViStoragePolicy>] [-SourceNetwork <VBRViNetworkInfo[]>] [-TargetNetwork <VBRViNetworkInfo[]>] [-VMName <string>] [-DiskType <EDiskCreationMode> {Source | Thick | Thin | ThickEagerZeroed}] [-PowerUp <bool>] [-SkipTagsRestore] [-Reason <string>] [-RunAsync] [-Credentials <CCredentials>] [-Force] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction> {DisableNetwork | AbortRecovery}] [-StagingApplicationGroup <CSbAppGroup>] [-StagingStartupOptions <VBRApplicationGroupStartupOptions>] [-NICsEnabled] [-Proxy <CViProxy[]>]  [<CommonParameters>] |

* Restore to original location.

|  |
| --- |
| Start-VBRRestoreVM -RestorePoint <COib> -ToOriginalLocation [-DiskType <EDiskCreationMode> {Source | Thick | Thin | ThickEagerZeroed}] [-PowerUp <bool>] [-SkipTagsRestore] [-Reason <string>] [-RunAsync] [-QuickRollback] [-StoragePolicyAction <VBRStoragePolicyAction> {Current | Stored | Default}] [-Credentials <CCredentials>] [-Force] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction> {DisableNetwork | AbortRecovery}] [-NICsEnabled] [-Proxy <CViProxy[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the entire VM restore. With this cmdlet, you can restore the VM with the following options:

* Restore to original location
* Restore to original location with different settings
* Restore to another location
* Staged restore
* Secure restore

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the VM restore point to which you want to restore. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByProperty Name) |
| Server | Specifies the ESXi host where you want to locate the restored VM.  Note: The cmdlet will not run if you specify this parameter with the ToOriginalLocation parameter. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 1 | False |
| EnableStagedRestore | For staged restore.  Enables the staged restore option. | SwitchParameter | True | Named | False |
| StagingCredentials | For staged restore.  Specifies the VM guest credentials for the staged restore. Veeam Backup & Replication will use these credentials for authenticating with the VM and run the script. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| StagingScript | For staged restore.  Specifies the script location. Veeam Backup & Replication will use this script to prepare VMs before the restore. | String | True | Named | False |
| StagingVirtualLab | For staged restore.  Specifies the virtual lab. The cmdlet will use this virtual lab to start VMs and run the script.  Specifies the virtual lab that you will use for staged restore. Veeam Backup & Replication will move VMs into the isolated environment and will run the staging script. | Accepts the ISbVirtualLab object. To get this object, run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. | True | Named | False |
| ResourcePool | For restore to another location.  Specifies the resource pool where you want to locate the restored VM. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | 2 | False |
| Datastore | For restore to another location.  Specifies the datastore to which you want to connect the restored VM. | Accepts the CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | 3 | False |
| StoragePolicy | Specifies the VMware storage policy profile that must be applied to the restored virtual disks. | Accepts [VBRViStoragePolicy](vbrvistoragepolicy.md) object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| Folder | For restore to another location.  Specifies the folder where you want to locate the restored VM. | Accepts the CViFolderItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| VMName | Specifies the name you want to apply to the restored VM.  By default, the original VM name is applied. | String | False | Named | False |
| DiskType | Specifies the disk type you want to apply to the restored VM:   * Thin * Thick * AsOriginal | EDiskCreationMode | False | Named | False |
| PowerUp | Defines that the restored VM will be powered up immediately after the restore.  Otherwise, you will have to power up the VM manually. | SwitchParameter | False | Named | False |
| SkipTagsRestore | Defines that the VM will be restored without its VMware tag.  Otherwise, the restored VM will keep its original tag. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing restore of the selected VM.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| QuickRollback | For restore to original location.  Defines that the incremental restore must be performed. | SwitchParameter | False | Named | False |
| ToOriginalLocation | Defines that the VM must be restored with original ResourcePool, Datastore and Folder settings.  Note: The cmdlet will not run if you specify this parameter with the Server parameter. | SwitchParameter | False | Named | False |
| StoragePolicyAction | Specifies the strategy for selecting storage policy profile in case the storage profile of the backed up VM differs from the profile of the original VM:   * Current: the restored VM will be subscribed to the same profile as in backup (if such profile still exists) or to the profile to which the original VM is subscribed (if profile as in backup was removed). * Default: the restored VM will be subscribed to the profile that is set as default for the target datastore. * Stored: the restored VM will be subscribed to the profile as in backup (if such profile still exists). | VBRStoragePolicyAction | False | Named | False |
| Force | Defines that the cmdlet will perform VM restore even if the geographic location of the repository where VM backups reside and the target host location do not match. | SwitchParameter | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the VM. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| SourceNetwork | For restore to another location.  Specifies the source site network. Veeam Backup & Replication will map it to the target network.  Note: This parameter is required if you specify the TargetNetwork parameter. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| TargetNetwork | For restore to another location.  Specifies the target site network. Veeam Backup & Replication will map it with the source network.  Note: This parameter is required if you specify the SourceNetwork parameter. | Accepts the VBRViNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| StagingApplicationGroup | For staged restore.  Specifies the application group that the cmdlet will use for staged restore. | Accepts the CSbAppGroup object. To get this object, run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. | False | Named | False |
| StagingStartupOptions | For staged restore.  Specifies startup settings of VMs that you want to restore. Veeam Backup & Replication will use these settings to start selected VMs after recovery. | Accepts the VBRApplicationGroupStartupOptions object. To create this object, run the [New-VBRApplicationGroupStartupOptions](new-vbrapplicationgroupstartupoptions_surebackup.md) cmdlet. | False | Named | False |
| EnableAntivirusScan | Enables the secure restore option. Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Defines that the antivirus will continue VMs scan after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies the secure restore action when the infection is detected.   * DisableNetwork - use this option if you want to restore VMs with disabled network adapters (NICs). * AbortRecovery - use this option if you want to cancel the restore session. | VBRVirusDetectionAction | False | Named | False |
| NICsEnabled | Defines that the restored VM will be connected to the network.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| Proxy | Specifies the backup proxy that the cmdlet will use during restore.  If you do not provide this parameter, the cmdlet will use select the backup proxy automatically. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named |  |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring VM to Original Location

|  |  |
| --- | --- |
| This example shows how to start restore of a VM to the original location.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  Start-VBRRestoreVM -RestorePoint $restorepoint -Reason "Test restore" -ToOriginalLocation -StoragePolicyAction Default |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRRestoreVM cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the Reason parameter value. * Provide the ToOriginalLocation parameter. * Set the Default value for the StoragePolicyAction parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring VM to Another Location

|  |  |
| --- | --- |
| This example shows how to restore a VM to another location.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  $server = Get-VBRServer -Name "north.support.local"  $rpool = Find-VBRViResourcePool -Server $server  $datastore = Find-VBRViDatastore -Server $server  Start-VBRRestoreVM –RestorePoint $restorepoint[1] –Server $server –ResourcePool $rpool –Datastore $datastore –PowerUp:$true -NICsEnabled:$false |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $rpool variable. 4. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $datastore variable. 5. Run the Start-VBRRestoreVM cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the second restore point is used.   * Set the $server variable as the Server parameter value. * Set the $rpool variable as the ResourcePool parameter value. * Set the $datastore variable as the Datastore parameter value. * Set the $true value for the PowerUp parameter. * Set the $false value to the NICsEnabled parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Staged Restore of VM

|  |  |
| --- | --- |
| The example shows how perform staged restore of the selected VM.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  $server = Get-VBRServer -Name "north.support.local"  $lab = Get-VSBVirtualLab -Name "VirtualLab"  $creds = Get-VBRCredentials -Name "Administrator"  Start-VBRRestoreVM -RestorePoint $restorepoint[0] -Server $server -StagingVirtualLab $lab -StagingScript "c:/script.cmd" -EnableStagedRestore -StagingCredentials $creds |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Get-VSBVirtualLab](get-vsbvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 4. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 5. Run the Start-VBRRestoreVM cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the first restore point is used.   * Set the $server variable as the Server parameter value. * Set the $lab variable as the StagingVirtualLab parameter value. * Specify the StagingScript parameter value. * Provide the EnableStagedRestore parameter. * Set the $creds variable as the StagingCredentials parameter value. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)
* [Find-VBRViFolder](find-vbrvifolder.md)
* [Get-VBRLocation](get-vbrlocation.md)

Page updated 12/10/2024

Page content applies to build 13.0.1.1071
