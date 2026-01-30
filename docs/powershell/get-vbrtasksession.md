---
title: "Get-VBRTaskSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtasksession.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTaskSession


Short Description

Returns tasks performed during job sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRTaskSession -Session <CBackupSession> [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns tasks performed during the specified session. The tasks are VMs processed during one job session.

Run the [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md) cmdlet to get the tasks for SureBackup jobs session.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the session tasks which you want to get. | Accepts the following objects:   * CBackupSession   To get this object, run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet.   * VBRSession   To get this object, run the [Get-VBRSession](get-vbrsession.md) cmdlet.   * VBRComputerBackupJobSession   To get this object, run the [Get-VBRComputerBackupJobSession](get-vbrcomputerbackupjobsession.md) cmdlet.   * VBREPSession   To get this object, run the [Get-VBREPSession](get-vbrepsession.md) cmdlet.   * VBRPluginBackupSession   To get this object, run the [Get-VBRPluginBackupSession](get-vbrpluginbackupsession.md) cmdlet.   * VBRTapeBackupSession   To get this object, run the [Get-VBRTapeBackupSession](get-vbrtapebackupsession.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Name | Specifies the array of job object names (for example, VMs in job). The cmdlet will return tasks performed for these objects during the selected session. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRTaskSession

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of Tasks Performed for VMs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get the list of tasks performed for the DC and DNS VMs in the backup job session with incremental backups named Exchange Backup.  |  | | --- | | Get-VBRBackupSession -Name "Exchange Backup (Incremental)" | Get-VBRTaskSession -Name "DC", "DNS" |  Perform the following steps:   1. Run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRTaskSession cmdlet. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting List of Tasks Performed for VMs [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get the list of tasks performed for the DC and DNS VMs in the backup job session with incremental backups named Exchange Backup.  |  | | --- | | $ExchangeSession = Get-VBRBackupSession -Name "Exchange Backup (Incremental)"  Get-VBRTaskSession -Session $ExchangeSession -Name "DC", "DNS" |  Perform the following steps:   1. Run the [Get-VBRBackupSession](get-vbrbackupsession.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeSession variable. 2. Run the Get-VBRTaskSession cmdlet. Set the $ExchangeSession variable as the Session parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRBackupSession](get-vbrbackupsession.md)


