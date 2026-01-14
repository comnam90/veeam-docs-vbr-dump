---
title: "Get-VBRAmazonRestoreSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazonrestoresession.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonRestoreSession

In this article

Short Description

Returns active restore sessions to Amazon EC2.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all active restore to Amazon EC2 sessions.

|  |
| --- |
| Get-VBRAmazonRestoreSession  [<CommonParameters>] |

* Get a specific restore to Amazon EC2 session.

|  |
| --- |
| Get-VBRAmazonRestoreSession -Session <VBRAmazonRestoreSession>  [<CommonParameters>] |

* Get active restore to Amazon EC2 sessions by ID.

|  |
| --- |
| Get-VBRAmazonRestoreSession [-Id <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns active restore to Amazon EC2 sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore to Amazon EC2 active session that you want to get. | VBRAmazonRestoreSession | True | Named | True (ByValue,  ByPropertyName) |
| Id | Specifies the ID of the restore to Amazon EC2 active session you want to get. | Guid | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRAmazonRestoreSession

Examples

This command gets the active restore session to Amazon EC2.

|  |
| --- |
| Get-VBRAmazonRestoreSession -Session "New session" |

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
