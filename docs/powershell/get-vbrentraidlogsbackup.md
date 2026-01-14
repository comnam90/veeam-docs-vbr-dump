---
title: "Get-VBREntraIDLogsBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidlogsbackup.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDLogsBackup

In this article

Short Description

Returns backups of Microsoft Entra ID logs.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all backups of Entra ID logs.

|  |
| --- |
| Get-VBREntraIDLogsBackup  [<CommonParameters>] |

* Get backups of logs by job names.

|  |
| --- |
| Get-VBREntraIDLogsBackup -Name <String[]>  [<CommonParameters>] |

* Get backups of logs by their IDs.

|  |
| --- |
| Get-VBREntraIDLogsBackup -Id <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backups of Entra ID audit and sign-in logs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of the backup job names. The cmdlet will return backups produced by these jobs. | String[] | True | Named | False |
| Id | Specifies an array of the backup IDs. The cmdlet will return backups with these IDs. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of [VBREntraIDLogsBackup](vbrentraidlogsbackup.md) objects that contain information about log backups.

Examples

Getting Entra ID Log Backup Job

This example shows how to get the Log Backup backup job.

|  |
| --- |
| $logBackup = Get-VBREntraIDLogsBackup -Name "Log Backup" |

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
