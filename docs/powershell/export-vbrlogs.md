---
title: "Export-VBRLogs"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrlogs.html"
last_updated: "1/12/2026"
product_version: "13.0.1.1071"
---

# Export-VBRLogs

In this article

Short Description

Collects system logs for export.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Collect logs for servers.

|  |
| --- |
| Export-VBRLogs -Server <CHost[]> -FolderPath <string> [-Compress] -LastDays <Int32>] [-Wait]  [<CommonParameters>] |

* Collect logs for jobs.

|  |
| --- |
| Export-VBRLogs -Job <IJob[]> -FolderPath <string> [-Compress] [-LastDays <Int32>] [-Wait]  [<CommonParameters>] |

* Collect logs for VMs.

|  |
| --- |
| Export-VBRLogs -Entity <IVmItem[]> -FolderPath <string> [-Compress] [-LastDays <Int32>] [-Wait]  [<CommonParameters>] |

* Collect logs for backups.

|  |
| --- |
| Export-VBRLogs -Backup <CBackup[]> -FolderPath <string> [-Compress] [-LastDays <Int32>] [-Wait]  [<CommonParameters>] |

* Collect logs for protected computers.

|  |
| --- |
| Export-VBRLogs -Computer <VBRDiscoveredComputer[]> -FolderPath <String> [-Compress] [-LastDays <Int32>] [-Wait]  [<CommonParameters>] |

* Collect logs for cloud tenants.

|  |
| --- |
| Export-VBRLogs -Tenant <VBRCloudTenant[]> -FolderPath <String> [-Compress] [-Wait] [-LastDays <Int32>]  [<CommonParameters>] |

* Collect logs for a scale-out backup repository.

|  |
| --- |
| Export-VBRLogs -ScaleOutRepository <CExtendableRepository[]> -FolderPath <String> [-Compress] [-Wait] [-LastDays <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet collects system logs. The log files are written to the folder you specify in this cmdlet.

You can use this cmdlet to collect logs you can send to the Veeam support.

You can get logs for all kind of virtual host, any jobs including SureBackup jobs, entities including VMware or Hyper-V VMs, or any backup. Use an appropriate parameter set for each case.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an array of servers. The cmdlet will collect logs from these servers.  Note: The selected servers must be running and available over the network. | Accepts the CHost[] object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Job | Specifies an array of jobs. The cmdlet will collect logs of these jobs.  Accepts all kinds of jobs. | Accepts the IJob[] object. To get this object, run one of the following cmdlets:   * [Get-VBRJob](get-vbrjob.md) * [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) * [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) * [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) * [Get-VBRTapeJob](get-vbrtapejob.md) | True | Named | True (ByValue, ByProperty Name) |
| Entity | Specifies an array of VMs. The cmdlet will collect logs of these VMs. | Accepts the IVmItem[] object. To get this object, run one of the following cmdlets:   * [Find-VBRViEntity](find-vbrvientity.md) * [Find-VBRHvEntity](find-vbrhventity.md) | True | Named | True (ByValue, ByProperty Name) |
| Backup | Specifies an array of backups. The cmdlet will collect logs of these backups. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Computer | Specifies an array of protected computers. The cmdlet will collect logs of these computers. | Accepts the VBRDiscoveredComputer[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Tenant | Specifies an array of cloud tenants. The cmdlet will collect logs of these cloud tenants.  Note: This parameter does not return logs of VMware Cloud Director and Active Directory tenant accounts. | Accepts the [VBRCloudTenant](vbrcloudtenant.md)[] object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| ScaleOutRepository | Specifies an array of scale-out backup repositories. The cmdlet will collect logs of these repositories. | Accepts the CExtendableRepository[]object. To get this object, run the [Get-VBRScaleOutBackupRepository](get-vbrscantasksession.md) cmdlets: | True | Named | True (ByValue, ByProperty Name) |
| FolderPath | Specifies the destination folder. The cmdlet will export  logs to this folder. | String | True | Named | False |
| Compress | Defines that the log files will be compressed.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| LastDays | Specifies the number of days for which to collect logs. If you do not specify this parameter, Veeam Backup & Replication will collect logs for the last 1 day. | Int32 | False | Named | False |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLogs object that contains system logs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Collecting Logs for Servers

|  |  |
| --- | --- |
| This example shows how to collect log files from the Active\_Directory server with the following settings:   * The destination path is C:\Logs. * The period for collecting data is last 7 days. * The logs compression is enabled.   |  | | --- | | $server = Get-VBRServer -Name "Active\_Directory"  Export-VBRLogs -Server $server -FolderPath "C:\Logs" -LastDays 7 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Export-VBRLogs cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value.  * Specify the FolderPath parameter value.  * Specify the LastDays parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Collecting Logs for Jobs

|  |  |
| --- | --- |
| This example shows how to collect log files for the DC SureJob SureBackup job with the following settings:   * The destination path is C:\Logs\SureBackup Logs. * The period for collecting data is not set to collect all the data for the job. * The logs compression is disabled.   |  | | --- | | $job = Get-VBRSureBackupJob -Name "DC SureJob"  Export-VBRLogs -Job $job -FolderPath "C:\Logs\SureBackup Logs" -Compress:$false |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.  1. Run the Export-VBRLogs cmdlet. Set the $job variable as the Job parameter value. Specify the FolderPath parameter value. Set the Compress parameter to $false. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Collecting Logs for VM

|  |  |
| --- | --- |
| This example shows how to collect log files for the DC VM with the following settings:   * The destination path is C:\Logs. * The period for collecting data is last 30 days.  * The logs compression is enabled.   |  | | --- | | $vm = Find-VBRViEntity -Name "DC"  Export-VBRLogs -Entity $vm -FolderPath "C:\Logs" -LastDays 30 |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable.  1. Run the Export-VBRLogs cmdlet. Specify the following settings:  * Set the $vm variable as the Entity parameter value.  * Specify the FolderPath parameter value.  * Specify the LastDays parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Collecting Logs for Backups

|  |  |
| --- | --- |
| This example shows how to collect log files for the srv2049-job backup with the following settings:   * The destination path is C:\Logs. * The period for collecting data is last 14 days.  * The logs compression is enabled.   |  | | --- | | $backup = Get-VBRBackup -Name "srv2049-job"  Export-VBRLogs -CBackup $backup -FolderPath "C:\Logs" -LastDays 14 |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.  1. Run the Export-VBRLogs cmdlet. Specify the following settings:  * Set the $backup variable as the CBackup parameter value.  * Specify the FolderPath parameter value.  * Specify the LastDays parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Collecting Logs for Protected Computers

|  |  |
| --- | --- |
| This example shows how to collect log files for protected computers with the following settings:   * The destination path is C:\Logs. * The period for collecting data is last 10 days.  * The logs compression is enabled.   |  | | --- | | $machines = Get-VBRDiscoveredComputer -Type Computer  Export-VBRLogs -Computer $machines[3] -FolderPath "C:\Logs" -LastDays 10 |  Perform the following steps:   1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the Computer option for the Type parameter. Save the result to the $machines variable.   The Get-VBRDiscoveredComputer cmdlet will return an array of protected computers. Mind the ordinal number of the necessary protected computer (in our example, it is the fourth computer in the array).   1. Run the Export-VBRLogs cmdlet. Specify the following settings:  * Set the $machines[3] variable as the Computer parameter value.  * Specify the FolderPath parameter value.  * Specify the LastDays parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRSureBackupJob](get-vbrsurebackupjob.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)

Page updated 1/12/2026

Page content applies to build 13.0.1.1071
