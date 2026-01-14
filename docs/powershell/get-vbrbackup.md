---
title: "Get-VBRBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackup.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Get-VBRBackup

In this article

Short Description

Returns backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all backups.

|  |
| --- |
| Get-VBRBackup [-VeeamZIP]  [<CommonParameters>] |

* Get backups by their ID.

|  |
| --- |
| Get-VBRBackup -Id <Guid[]> [-VeeamZIP]  [<CommonParameters>] |

* Get backups by their name.

|  |
| --- |
| Get-VBRBackup [-Name <String[]>] [-VeeamZIP]  [<CommonParameters>] |

Detailed Description

This cmdlet returns backups created with Veeam Backup & Replication.

|  |
| --- |
| Note |
| The backups contain all restore points for all machines that are processed by the job. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of the backup IDs. The cmdlet will return backups with these IDs. | Guid[] | True | Named | True (ByPropertyName) |
| Name | Specifies an array of the job name. The cmdlet will return backups produced with these jobs. | String[] | False | Named | False |
| VeeamZIP | Defines that the cmdlet will return VeeamZIP backups. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackup object that contains backups created with Veeam Backup & Replication.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Backups

|  |  |
| --- | --- |
| This command returns all backups created with Veeam Backup & Replication.  |  | | --- | | Get-VBRBackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backups by ID

|  |  |
| --- | --- |
| This command returns the d6b08a78-f405-400a-bb02-a132cf1778fa backup.  |  | | --- | | Get-VBRBackup -Id "d6b08a78-f405-400a-bb02-a132cf1778fa" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Backups by Name

|  |  |
| --- | --- |
| This command returns the Cloud Webservices Backup and Exchange Backup\_imported backups.  |  | | --- | | Get-VBRBackup -Name "Cloud Webservices Backup", "Exchange Backup\_imported" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting VeeamZIP Backup

|  |  |
| --- | --- |
| This command returns the VeeamZIP backups.  |  | | --- | | Get-VBRBackup -VeeamZIP | |

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
