---
title: "Get-VBRComputerBackupJobSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcomputerbackupjobsession.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Get-VBRComputerBackupJobSession


Short Description

Returns jobs sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Veeam Agent job sessions by the job name.

|  |
| --- |
| Get-VBRComputerBackupJobSession [-Name <string[]>]  [<CommonParameters>] |

* Get Veeam Agent job sessions by the sessions ID.

|  |
| --- |
| Get-VBRComputerBackupJobSession [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns job sessions. You can get sessions of Veeam Agent jobs that are managed by Veeam Backup & Replication and Veeam Agent backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for Veeam Agent jobs. The cmdlet will return sessions with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Id | Specifies an array of IDs for Veeam Agent job sessions. The cmdlet will return the sessions with these IDs. | Guid[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSession object that contains settings of sessions that are running by Veeam Agent backup jobs and Veeam Agent backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Agent Jobs Sessions by Name

|  |  |
| --- | --- |
| This command returns the Windows backup policy Agent job session.  |  | | --- | | Get-VBRComputerBackupJobSession -Name "Windows backup policy" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Get Agent Jobs Sessions by ID

|  |  |
| --- | --- |
| This command returns the 1137c678-e79d-48c4-8d30-b921a612ba1e Agent job session.  |  | | --- | | Get-VBRComputerBackupJobSession -Id 1137c678-e79d-48c4-8d30-b921a612ba1e | |


