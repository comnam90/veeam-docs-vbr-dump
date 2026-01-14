---
title: "Start-VBRScanBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrscanbackup.html"
last_updated: "8/1/2025"
product_version: "13.0.1.1071"
---

# Start-VBRScanBackup

In this article

Short Description

Starts a scan of backups with antivirus or YARA scan.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRScanBackup -Object <VBRBackupObject[]> -ScanMode <VBRRestorePointScanMode> [-EnableAntivirusScan] [-EnableYARAScan] [-YARARule <String>] [-FromPointInTime <DateTime>] [-ToPointInTime <DateTime>] [-EnableEntireImageScan] [-RunAsync] [-RestorePoint <VBRRestorePoint>] [<CommonParameters>] |

Detailed Description

This cmdlet starts a scan of backups with antivirus or YARA scan. You can scan the following types of backups:

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication.
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication.
* Backups created by backup copy jobs.

* Backups of Nutanix AHV virtual machines created by [Veeam Backup for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=6).

* Backups of RHV VMs created by [Veeam Backup for RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=6).
* Backups of Windows machines created by Veeam Agent for Microsoft Windows.
* Backup of VMware Cloud Director VMs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Object | Specifies an array of backups that you want to scan. | Accepts the VBRBackupObject[] object. To create this object, run the [Get-VBRBackupObject](get-vbrbackupobject.md) cmdlet. | True | Named | False |
| ScanMode | Specifies one of the following scan modes:   * AllInInterval — Use this mode to scan backup content with necessary YARA rules. The cmdlet will scan all restore points sequentially and will initiate a malware event. * FirstInInterval — Use this mode if you are not sure when the attack started. The cmdlet will scan restore points in optimal order until it finds the malware-free restore point. * MostRecent — Use this mode if you consider that a cyber-attack started recently. The cmdlet will scan the restore points sequentially, starting from the most resent restore point, until it finds the latest malware-free restore point. | VBRRestorePointScanMode | True | Named | False |
| EnableAntivirusScan | Enables secure restore.  If you provide this parameter, Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore.  Default: False. | SwitchParameter | False | Named | False |
| EnableYARAScan | Defines that Veeam Backup & Replication will scan VMs with the specified YARA rule.  If you do not provide this parameter, Veeam Backup & Replication will not scan VMs with the YARA rule.  Use the YARARule parameter to specify the YARA rule.  Default: False. | SwitchParameter | False | Named | False |
| YARARule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| FromPointInTime | Specifies the date and time. The cmdlet will scan backups that were created starting from this date and time. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | False | Named | False |
| ToPointInTime | Specifies the date and time. The cmdlet will scan backups that were created by this date and time. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | False | Named | False |
| EnableEntireImageScan | Defines that the cmdlet will scan all restore points in backup even after it finds the first affected restore point.  Default: False. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| RestorePoint | Specifies a restore point that you want to scan. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSureBackupJobSession](vbrsurebackupjobsession.md)

Examples

Scanning Backups with YARA Scan

This example shows how scan backups with YARA scan.

|  |
| --- |
| $yararule = Get-VBRYARARule  $backup = Get-VBRBackup  $vmbackup = Get-VBRBackupObject -Backup $backup[0]  Start-VBRScanBackup -Object $vmbackup[0] -ScanMode FirstInInterval -EnableYARAScan -YARARule $yararule[0] |

Perform the following steps:

1. Run the [Get-VBRYARARule](get-vbryararule.md) cmdlet. Save the result to the $yararule variable.
2. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Save the result to the $backup variable.
3. Run the [Get-VBRBackupObject](get-vbrbackupobject.md) cmdlet. Set the $backup[0] variable as the Backup parameter value. Save the result to the $vmbackup variable.

The Get-VBRBackupObject cmdlet will return an array of VM backups. Mind the ordinal number of the necessary VM backup (in our example, it is the first VM backup in the array).

1. Run the Start-VBRScanBackup cmdlet. Specify the following settings:

* Set the $vmbackup[0] variable as the Object parameter value.
* Set the FirstInInterval option for the ScanMode parameter.
* Provide the EnableYARAScan parameter.
* Set the $yararule[0] variable as the YARARule parameter value.

Related Commands

* [Get-VBRYARARule](get-vbryararule.md)
* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRBackupObject](get-vbrbackupobject.md)

Page updated 8/1/2025

Page content applies to build 13.0.1.1071
