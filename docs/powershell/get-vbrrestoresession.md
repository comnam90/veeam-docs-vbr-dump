---
title: "Get-VBRRestoreSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrestoresession.html"
last_updated: "12/18/2023"
product_version: "13.0.1.1071"
---

# Get-VBRRestoreSession

In this article

Short Description

Returns restore sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get restore sessions of specific VMs.

|  |
| --- |
| Get-VBRRestoreSession [-Name <string[]>]  [<CommonParameters>] |

* Get restore sessions with specific IDs.

|  |
| --- |
| Get-VBRRestoreSession [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore sessions stored in Veeam Backup & Replication database.

You can get the list of all restore sessions or get the restore sessions of a specific VM or VMs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of VM names. The cmdlet will return the restore sessions of these VMs. | String[] | False | Named | False |
| Id | Specifies the array of the restore sessions IDs. The cmdlet will return the restore sessions with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Restore Sessions in Database

|  |  |
| --- | --- |
| This command looks for all restore sessions stored in the database.  |  | | --- | | Get-VBRRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Sessions of Specific VMs

|  |  |
| --- | --- |
| This command looks for the restore sessions of the Hv\_DNS and Hv\_DC VMs.  |  | | --- | | Get-VBRRestoreSession -Name "Hv\_DNS", "Hv\_DC" | |

Page updated 12/18/2023

Page content applies to build 13.0.1.1071
