---
title: "Get-VESQLRDSBackup"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlrdsbackup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLRDSBackup


Short Description

Returns backups of Amazon RDS instances for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLRDSBackup [-Name <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backups of Amazon RDS instances for Microsoft SQL Server.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Name | Specifies an array of backup names. The cmdlet will return backups with these names.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRDSBackup](vesqlrdsbackup.md)[] object that contains an array of backups of Amazon RDS instances for Microsoft SQL Server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Backups of Amazon RDS Instances for Microsoft SQL Server

|  |  |
| --- | --- |
| This command returns all backups of Amazon RDS instances for Microsoft SQL Server.  |  | | --- | | Get-VESQLRDSBackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Backup of Amazon RDS Instance for Microsoft SQL Server

|  |  |
| --- | --- |
| This command returns backups of Amazon RDS instances for Microsoft SQL Server that have specific names. Use the wildcard \* character to get all backups whose names begin with "RDS".  |  | | --- | | Get-VESQLRDSBackup -Name "RDS\*" | |

Page updated 2026-01-27

