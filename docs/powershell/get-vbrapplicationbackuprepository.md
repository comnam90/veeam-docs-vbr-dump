---
title: "Get-VBRApplicationBackupRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationbackuprepository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRApplicationBackupRepository


Short Description

Returns application backup repositories.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an application backup repository by ID.

|  |
| --- |
| Get-VBRApplicationBackupRepository -Id <Guid[]>  [<CommonParameters>] |

* Get an application backup repository by name.

|  |
| --- |
| Get-VBRApplicationBackupRepository [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of application backup repositories added to the backup infrastructure.

You can get a list of all backup repositories or look for repositories directly by name or ID.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Id | Specifies the array of IDs of application backup repositories that you want to get. | GUID[] | True | Named | False |
| Name | Specifies the array of names of application backup repositories that you want to get. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the [VBRApplicationBackupRepository](vbrapplicationbackuprepository.md)[] object that contains settings of application backup repositories.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Application Backup Repositories

|  |  |
| --- | --- |
| This command gets all application backup repositories added to the backup infrastructure.  |  | | --- | | Get-VBRApplicationBackupRepository | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Application Backup Repositories by Name

|  |  |
| --- | --- |
| This command gets the Application Backup Repository 01 application backup repository.  |  | | --- | | Get-VBRApplicationBackupRepository -Name "Application Backup Repository 01" | |

Page updated 2026-06-04

