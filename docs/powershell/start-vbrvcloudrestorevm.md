---
title: "Start-VBRvCloudRestoreVm"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcloudrestorevm.html"
last_updated: "12/6/2024"
product_version: "13.0.1.1071"
---

# Start-VBRvCloudRestoreVm

In this article

Short Description

Starts a Cloud Director VM restore.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a Cloud Director VM restore to original location.

|  |
| --- |
| Start-VBRvCloudRestoreVm -RestorePoint <COib> [-PowerUp] [-Reason <String>] [-RunAsync] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction>] [-EnableVmTagsRestore]  [<CommonParameters>] |

* Start a Cloud Director VM restore to another location.

|  |
| --- |
| Start-VBRvCloudRestoreVm -RestorePoint <COib> -vApp <CVcdVappItem> [-StorageProfile <CVcdOrgVdcStorageProfile>] [-vCloudDatastore <CVcdDatastoreRestoreInfo>] [-VmTemplate <IVcdItem>] [-VMName <String>] [-PowerUp] [-Reason <String>] [-RunAsync] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction>] [-EnableVmTagsRestore]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session of a selected Cloud Director VM. With this cmdlet, you can perform the following recover scenarios:

* Restore to the original location
* Restore to another location
* Restore with different settings

* Secure restore of the selected restore point

To restore a VM to the original location you only need to select the required restore point. Be careful to specify the restore point of the VM, not the vApp which is not a valid value for this cmdlet. Veeam Backup & Replication gets all the information needed for restore from the restore point data.

You cannot restore multiple VM with one command, to restore several VMs you need to start a restore session for each one.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the VM. If you specify no other parameters of the VM, it will be restored with its initial settings, i.e. the datastore or VM template.  This parameter does not accept VM arrays. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| vApp | Specifies the vApp where to you want to restore the VM. | Accepts the CVcdVappItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| StorageProfile | Specifies the storage profile you want to apply to the restored VM. | Accepts the CVcdOrgVdcStorageProfile object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| vCloudDatastore | Specifies the datastore you want to use with the restored VM. | Accepts the CVcdDatastoreRestoreInfo object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| VmTemplate | Specifies the template you want to apply to the restored VM. | Accepts the IVcdItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| VMName | Specifies the VM name you want to apply to the restored VM. | String | False | Named | False |
| PowerUp | If set, the VM will be powered up right after it is restored. Otherwise you will need to power up the VM manually. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing restore of the selected VM.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| EnableAntivirusScan | Defines that the cmdlet will perform secure restore. Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Enables the antivirus scan for all volumes of the infected restore point. Use this option if you want to perform secure restore with the following options:   * Continue machine scan after the first virus threat is found * Get the report on all virus threats | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies secure restore action when the virus threat is detected.   * DisableNetwork - use this option if you want to restore VMs in safe state with disabled network adapters (NICs). * AbortRecovery - use this option if you want to cancel the restore session. | VBRVirusDetectionAction | False | Named | False |
| EnableVmTagsRestore | Defines that the cmdlet will restore VM tags. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Cloud VM Restore to Original Location

|  |  |
| --- | --- |
| The example shows how to start a Cloud Director VM restore to the original location.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  Start-VBRvCloudRestoreVm -RestorePoint $restorepoint[1] |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCloudRestoreVm cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.   The [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the second restore point in the array). |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Cloud VM Restore to Another vApp

|  |  |
| --- | --- |
| The example shows how to restore a VM to another vApp with another storage profile.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  $vapp = Find-VBRvCloudEntity -VApp  $profile = Find-VBRvCloudEntity -StorageProfile  Start-VBRvCloudRestoreVm -RestorePoint $restorepoint -vApp $vapp -StorageProfile $profile |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the VApp parameter value. Save the result to the $vapp variable. 3. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the StorageProfile parameter value. Save the result to the $profile variable. 4. Run the Start-VBRvCloudRestoreVm cmdlet. Set the $restorepoint as the RestorePoint parameter value. Set the $vapp as the vApp parameter value. Set the $profile as the StorageProfile parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Secure Cloud VM Restore

|  |  |
| --- | --- |
| The example shows how to run secure restore of the selected VM. The job will run with the following settings:   * Veeam Backup & Replication will scan all volumes of the infected restore points.  * In case the infection is detected, Veeam Backup & Replication will restore the VM with disabled NIC.  * The RunAsync parameter is set to bring the process to the background.   |  | | --- | | $restorepoint = Get-VBRRestorePoint  Start-VBRvCloudRestoreVm -RestorePoint $restorepoint[1] -RunAsync -EnableAntivirusScan -EnableEntireVolumeScan -VirusDetectionAction DisableNetwork |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCloudRestoreVm cmdlet.  Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Provide the RunAsync parameter. * Provide the EnableAntivirusScan parameter. * Provide the EnableEntireVolumeScan parameter. * Set the DisableNetwork option for the VirusDetectionAction parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)

Page updated 12/6/2024

Page content applies to build 13.0.1.1071
