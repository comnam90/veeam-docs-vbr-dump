---
title: "Start-VBRViInstantVMDiskRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrviinstantvmdiskrecovery.html"
last_updated: "12/6/2024"
product_version: "13.0.1.1071"
---

# Start-VBRViInstantVMDiskRecovery


Short Description

Starts restore of VM virtual disks from backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRViInstantVMDiskRecovery -RestorePoint <COib> [-ShareCredentials <CCredentials>] -TargetVM <CViVmItem> -TargetVirtualDevice  <VBRViVirtualDevice[]> [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-Reason <string>] [-RunAsync] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts restore of VM virtual disks from backups. You can publish these to the production environment immediately after performing the restore.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of VMs. The cmdlet will restore virtual disks of these VMs. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| TargetVM | Specifies a target VM. The cmdlet will restore virtual disks to the specified VM. | Accepts the CViVmItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| TargetVirtualDevice | Specifies an array of target VM device nodes. The cmdlet will map the virtual disks from backup to the specified node. | Accepts the VBRViVirtualDevice[] object. To get this object, run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. | True | Named | False |
| ShareCredentials | For restore to different VM.  Specifies credentials that you want to use to authenticate with the VM to which you attach restored virtual disks. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| EnableAntivirusScan | Defines that the cmdlet will perform secure restore. Veeam Backup & Replication will trigger the antivirus software to scan selected VM virtual disks before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Defines that the antivirus will continue scan of VM virtual disks after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| Reason | Specifies a reason for performing instant recovery of VM virtual disks. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform restore of VM virtual disks even if the geographic location of the repository where backups of VM virtual disks reside and the target host location does not match. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the InstantRecovery object that contains details on virtual disks of VMs from backups.

Examples

Restoring VM Virtual Disks From Backups

This example shows how to restore VM virtual disks from the Winsrv4515 backup. The cmdlet will restore virtual disks of the Winsrv4515 VM.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint  $server = Get-VBRServer -Name "ESXiHost"  $vm = Find-VBRViEntity -Server $server -Name "Winsrv4515"  $device = Get-VBRViVirtualDevice -RestorePoint $restorepoint  Start-VBRViInstantVMDiskRecovery -RestorePoint $restorepoint[3] -TargetVM $vm -TargetVirtualDevice $device |

Perform the following steps:

1. Get the restore point:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point will be used.

1. Get the VM.

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $vm variable.

1. Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.

1. Run the Start-VBRViInstantVMDiskRecovery cmdlet. Specify the following settings:

* Set the $restorepoint variable as the RestorePoint parameter value.
* Set the $vm variable as the TargetVM parameter value.
* Set the $device variable as the TargetVirtualDevice parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)


