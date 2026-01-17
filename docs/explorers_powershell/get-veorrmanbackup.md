---
title: "Get-VEORRMANBackup"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veorrmanbackup.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns backups created by Veeam Plug-in for Oracle RMAN.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORRMANBackup [-Name <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backups created by Veeam Plug-in for Oracle RMAN.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of backup names. The cmdlet will return RMAN plug-in backups with these names.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [IVEORRMANBackup](veorrmanbackup.md)[] array that contains backups created by Veeam Plug-in for Oracle RMAN.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All RMAN Plug-in Backups

|  |  |
| --- | --- |
| This command returns all backups created by Veeam Plug-in for Oracle RMAN.  |  | | --- | | Get-VEORRMANBackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific RMAN Plug-in Backups

|  |  |
| --- | --- |
| This command returns RMAN plug-in backups with specific names. Use the wildcard \* character to get all backups whose names begin with "Oracle RMAN".  |  | | --- | | Get-VEORRMANBackup -Name "Oracle RMAN\*" | |

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
