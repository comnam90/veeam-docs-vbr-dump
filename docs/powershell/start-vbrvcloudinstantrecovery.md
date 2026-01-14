---
title: "Start-VBRvCloudInstantRecovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcloudinstantrecovery.html"
last_updated: "12/6/2024"
product_version: "13.0.1.1071"
---

# Start-VBRvCloudInstantRecovery

In this article

Short Description

Starts an instant recovery of Cloud Director VMs

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRvCloudInstantRecovery -RestorePoint <COib> [-vApp <CVcdVappItem>] [-VmName <string>] [-Datastore <CVcdDatastoreRestoreInfo>] [-PowerOn] [-Reason <string>] [-RunAsync] [-EnableTagRestore] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction> {DisableNetwork | AbortRecovery}]  [<CommonParameters>] |

Detailed Description

This cmdlet performs instant recovery of the selected Cloud Director VM. With this cmdlet, you can perform the following recover scenarios:

* Restore to the original location
* Restore to another vApp
* Secure restore of the selected restore point

To restore the VM to another vApp specify the required vApp object for the vApp parameter. To perform restore to the original location, omit this parameter.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the VM. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| vApp | Specifies the vApp that you want to restore the VM to.  Note: This parameter is required if you restore the VM to a new location, or with different settings. If you do not specify this parameter, Veeam Backup & Replication restores the VM with its initial settings and to its original location. | Accepts the CVcdVappItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| VmName | Specifies the name under which the VM should be restored and registered. By default, the original name of the VM is used.  If you are restoring the VM to the same vApp where the original VM is registered and the original VM still resides there, you must change the VM name.  Note: This parameter applies only if you restore the VM to a new location or with different settings. | String | False | Named | False |
| Datastore | Specifies the datastore you want to connect the restored VM to. If ommited, the VM will be connected to the original datastore.  Note: If you restore the VM to another vApp, make sure that the datastore is available in the Organization Cloud Director hosting the vApp to which the VM is restored. | Accepts the CVcdDatastoreRestoreInfo object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| PowerOn | Defines that the VM will be powered up right after it is restored. Otherwise you will need to power up the VM manually. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for performing restore of the selected VM.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| EnableAntivirusScan | Defines that the cmdlet will perform secure restore. Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Enables the antivirus scan for all volumes of the infected restore point. Use this option if you want to perform secure restore with the following options:   * Continue machine scan after the first virus threat is found. * Get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies secure restore action when the virus threat is detected.   * DisableNetwork - use this option if you want to restore VMs in safe state with disabled network adapters (NICs). * AbortRecovery - use this option if you want to cancel the restore session. | VBRVirusDetectionAction | False | Named | False |
| EnableTagRestore | Defines that Veeam Backup & Replication will restore VMware tags. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* VBRvCloudInstantRecoveryObject
* InstantRecovery

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Instant Recovery of Cloud VM

|  |  |
| --- | --- |
| The example shows how to start instant recovery of the Cloud Director VM.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  Start-VBRvCloudInstantRecovery -RestorePoint $restorepoint[1] |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCloudInstantRecovery cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.   The [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the second restore point in the array). |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Instant Recovery of Cloud VM to Specific Datastore

|  |  |
| --- | --- |
| The example shows how to start instant recovery of the Cloud Director VM. The job will run with the following settings:   * The VmName parameter is omitted to restore the VM with its original name. * The PowerOn parameter is set to power up the VM automatically right after it is restored. * The RunAsync parameter is set to bring the process to the background.   |  | | --- | | $restorepoint = Get-VBRRestorePoint  $vApp = Find-VBRvCloudEntity -vApp -Name "RestoreVapp"  $datastore = Find-VBRViDatastore -Name "Datastore05"  Start-VBRvCloudInstantRecovery -RestorePoint $restorepoint[1] -vApp $vapp -Datastore $datastore -PowerOn -Reason "Configuration test" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the vApp parameter. Specify the Name parameter value. Save the result to the $vapp variable. 3. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Name parameter value. Save the result to the $datastore variable. 4. Run the Start-VBRvCloudInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the second restore point in the array).   * Set the $vapp variable as the vApp parameter value. * Set the $datastore variable as the Datastore parameter value. * Provide the PowerOn parameter. * Specify the Reason parameter value. * Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Secure Restore of Selected Cloud VM

|  |  |
| --- | --- |
| The example shows how to run the secure restore of the selected Cloud Director VM. The job will run with the following settings:   * Veeam Backup & Replication will scan all volumes of the infected restore points. * In case the infection is detected, Veeam Backup & Replication will stop the instant recovery job.  * The RunAsync parameter is set to bring the process to the background.   |  | | --- | | $restorepoint = Get-VBRRestorePoint  Start-VBRvCloudInstantRecovery -RestorePoint $restorepoint[1] -RunAsync -EnableAntivirusScan -EnableEntireVolumeScan -VirusDetectionAction AbortRecovery |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRvCloudInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Provide the RunAsync parameter. * Provide the EnableAntivirusScan parameter. * Provide the EnableEntireVolumeScan parameter. * Set the AbortRecovery option for the VirusDetectionAction parameter to cancel the restore session in case the antivirus detects the virus threat. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)

Page updated 12/6/2024

Page content applies to build 13.0.1.1071
