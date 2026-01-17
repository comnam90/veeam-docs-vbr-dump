---
title: "Get-VESQLPluginBackup"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlpluginbackup.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Get-VESQLPluginBackup


Short Description

Returns backups created with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLPluginBackup [-Name <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backups created with Veeam Plug-in for Microsoft SQL Server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of backup names. The cmdlet will return SQL plug-in backups with these names.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [IVESQLPluginBackup](vesqlpluginbackup.md)[] object that contains an array of backups created with Veeam Plug-in for Microsoft SQL Server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Plug-in Backups

|  |  |
| --- | --- |
| This command returns all backups created with Veeam Plug-in for Microsoft SQL Server.  |  | | --- | | Get-VESQLPluginBackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific SQL Plug-in Backups

|  |  |
| --- | --- |
| This command returns SQL plug-in backups with specific names. Use the wildcard \* character to get all backups whose names begin with "SQL Backup".  |  | | --- | | Get-VESQLPluginBackup -Name "SQL Backup\*" | |


