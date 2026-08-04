---
title: "Start-VBRScanUnstructuredBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrscanunstructuredbackup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRScanUnstructuredBackup


Short Description

Starts a scan of file backups and object storage backups with antivirus or YARA scan.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRScanUnstructuredBackup -Backup <VBRUnstructuredBackup> -ScanMode <VBRRestorePointScanMode> [-RestorePoint <VBRUnstructuredBackupRestorePoint>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARARule <String>] [-FromPointInTime <DateTime>] [-ToPointInTime <DateTime>] [-EnableEntireImageScan] [-RunAsync] [<CommonParameters>] |

Detailed Description

This cmdlet starts an on-demand scan of file backup or object storage backup restore points with Veeam Threat Hunter or YARA scan. Veeam Backup & Replication inspects unstructured data stored in NAS backup repositories for malware and suspicious files.

An on-demand scan always runs as a full scan: the cmdlet enumerates all files in the restore point regardless of prior scan history.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Backup | Specifies the file backup or object storage backups that you want to scan. | Accepts the VBRUnstructuredBackup object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | False |
| ScanMode | Specifies one of the following scan modes:   * AllInInterval — Use this mode to scan all restore points in the specified interval sequentially. * FirstInInterval — Use this mode if you are not sure when the attack started. The cmdlet will scan restore points in optimal order until it finds the malware-free restore point. * MostRecent — Use this mode if you consider that a cyber-attack started recently. The cmdlet will scan the restore points sequentially, starting from the most recent restore point, until it finds the latest malware-free restore point. * Specific — Use this mode to scan a specific restore point. If you use this mode, you must provide the RestorePoint parameter. | VBRRestorePointScanMode | True | Named | False |
| RestorePoint | Specifies the restore point that you want to scan. Use this parameter when the ScanMode parameter is set to Specific. | Accepts the VBRUnstructuredBackupRestorePoint object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | False | Named | False |
| EnableAntivirusScan | Defines that Veeam Backup & Replication will scan the file backup or object storage backup restore point with Veeam Threat Hunter or a configured third-party antivirus engine.  You must provide at least one of the following parameters: EnableAntivirusScan or EnableYARAScan.  Default: False. | SwitchParameter | False | Named | False |
| EnableYARAScan | Defines that Veeam Backup & Replication will scan the file backup or object storage backup restore point with the specified YARA rule.  If you do not provide this parameter, Veeam Backup & Replication will not scan the restore point with a YARA rule.  Use the YARARule parameter to specify the YARA rule.  Default: False. | SwitchParameter | False | Named | False |
| YARARule | Specifies the YARA rule. Veeam Backup & Replication will scan the file backup or object storage backup restore point with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| FromPointInTime | Specifies the date and time. The cmdlet will scan restore points that were created starting from this date and time. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | False | Named | False |
| ToPointInTime | Specifies the date and time. The cmdlet will scan restore points that were created by this date and time. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | False | Named | False |
| EnableEntireImageScan | Defines that the cmdlet will scan all restore points in the NAS backup even after it finds the first affected restore point.  Note: For unstructured backups, the cmdlet always enumerates all files in each scanned restore point regardless of the value you set. The parameter is preserved for compatibility with the base scan workflow.  Default: False. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSureBackupJobSession](vbrsurebackupjobsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Scanning NAS Backup with Antivirus Scan

|  |  |
| --- | --- |
| This example shows how to scan the most recent restore point of a file backup or object storage backup with the antivirus scan.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "FileShare Backup"  Start-VBRScanUnstructuredBackup -Backup $backup -ScanMode MostRecent -EnableAntivirusScan |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Start-VBRScanUnstructuredBackup cmdlet. Specify the following settings:  * Set the $backup variable as the Backup parameter value. * Set the MostRecent value as the ScanMode parameter value. * Provide the EnableAntivirusScan parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Scanning Specific NAS Restore Point with YARA Rule

|  |  |
| --- | --- |
| This example shows how to scan a specific NAS restore point with a YARA rule.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "FileShare Backup"  $point = Get-VBRUnstructuredBackupRestorePoint -Backup $backup  Start-VBRScanUnstructuredBackup -Backup $backup -ScanMode Specific -RestorePoint $point[0] -EnableYARAScan -YARARule "ransomware.yar" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $point variable. 3. Run the Start-VBRScanUnstructuredBackup cmdlet. Specify the following settings:  * Set the $backup variable as the Backup parameter value. * Set the Specific value as the ScanMode parameter value. * Set the $point[0] variable as the RestorePoint parameter value. * Provide the EnableYARAScan parameter. * Specify the YARARule parameter value. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)

Page updated 2026-07-01

