---
title: "Get-VBRApplicationBackupJobSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationbackupjobsession.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBRApplicationBackupJobSession

In this article

Short Description

Returns job sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get application backup policy sessions by the job name.

|  |
| --- |
| Get-VBRApplicationBackupJobSession [-Name <string[]>]  [<CommonParameters>] |

* Get application backup policy by the sessions ID.

|  |
| --- |
| Get-VBRApplicationBackupJobSession [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns job sessions of application backup policies that are managed by Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for application policy sessions. The cmdlet will return sessions with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Id | Specifies an array of IDs for application policy sessions. The cmdlet will return the sessions with these IDs. | Guid[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSession object that contains settings of sessions that are running by application backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Application Policy Sessions by Name

|  |  |
| --- | --- |
| This command returns the Database backup policy application policy session.  |  | | --- | | Get-VBRApplicationBackupJobSession -Name "Database backup policy" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Application Policy Sessions by ID

|  |  |
| --- | --- |
| This command returns the 1137c678-e79d-48c4-8d30-b921a612ba1e application policy session.  |  | | --- | | Get-VBRApplicationBackupJobSession -Id 1137c678-e79d-48c4-8d30-b921a612ba1e | |

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
