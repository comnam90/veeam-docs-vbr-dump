---
title: "Start-VBRComputerVolumeRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcomputervolumerestore.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---

# Start-VBRComputerVolumeRestore


Short Description

Starts restore to original location of computer volumes backed-up with Veeam Agent for Microsoft Windows.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRComputerVolumeRestore -RestorePoint <COib> [-Volumes <VBRComputerDiskPartition[]>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-Reason <string>] [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts restore to original location of computer volumes backed-up with Veeam Agent for Microsoft Windows.

|  |
| --- |
| Important |
| Consider the following:   * The cmdlet does not support the disk mapping option. All disks are restored to the original location. * Restore of system OS volumes to original location is not supported. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of computers. The cmdlet will restore volumes these computers. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Volumes | Specifies an array of computer volumes that you want to restore. | Accepts the VBRComputerDiskPartition[] object. To get this object, run the [Get-VBRComputerDiskPartition](get-vbrcomputerdiskpartition.md) cmdlet. | False | Named | False |
| EnableAntivirusScan | Enables the option to perform secure restore.  If you provide this parameter, Veeam Backup & Replication will trigger the antivirus software to scan selected computer volumes before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Defines that the antivirus will continue computer volumes scan after the first virus threat is found. If you provide this parameter, the cmdlet will generate a report on all virus threats. | SwitchParameter | False | Named | False |
| Reason | Specifies a reason of volume-level restore.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| Force | Defines that the cmdlet will start restore without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Starting Restore to Original Location of Computer Volumes Backed-Up with Veeam Agent for Microsoft Windows

This example shows how to start a volume-level restore of the WinLaptop2017 computer.

|  |
| --- |
| $backup = Get-VBRBackup -Name "WinLaptop2017\*"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $volume = Get-VBRComputerDiskPartition -RestorePoint $restorepoint[3]  Start-VBRComputerVolumeRestore -RestorePoint $restorepoint[3] -Volumes $volume[2] -EnableAntivirusScan -EnableEntireVolumeScan -Force |

Perform the following steps:

1. Get the restore point:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.

Note: To get a list of restore points for a Veeam Agent job, you must provide the asterisks sign for the Name parameter value: Name "AgentJob\*". Otherwise, the Get-VBRRestorePoint cmdlet will not return any restore points for the Veeam Agent job.

1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).

1. Run the [Get-VBRComputerDiskPartition](get-vbrcomputerdiskpartition.md) cmdlet. Set the $restorepoint[3] variable as the RestorePoint parameter value. Save the result to the $volume variable.

The Get-VBRComputerDiskPartition cmdlet will return an array of volumes. Mind the ordinal number of the necessary volumes (in our example, it is the third volume in the array).

1. Run the Start-VBRComputerVolumeRestore cmdlet. Specify the following settings:

* Set the $restorepoint[3] variable as the RestorePoint parameter value.
* Set the $volume[2] variable as the Volumes parameter value.
* Provide the EnableAntivirusScan parameter.
* Provide the EnableEntireVolumeScan parameter.
* Provide the Force parameter.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRComputerDiskPartition](get-vbrcomputerdiskpartition.md)


