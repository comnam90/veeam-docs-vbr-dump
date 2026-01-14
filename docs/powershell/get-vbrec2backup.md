---
title: "Get-VBREC2Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrec2backup.html"
last_updated: "1/8/2024"
product_version: "13.0.1.1071"
---

# Get-VBREC2Backup

In this article

Short Description

Returns EC2 instance backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBREC2Backup [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of EC2 instance backups.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for EC2 instance backups. The cmdlet will return backups with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBREC2Backup object that contains an array of EC2 instance backups.

Examples

Getting EC2 Instance Backups

This command returns all EC2 instance backups.

|  |
| --- |
| Get-VBREC2Backup |

Page updated 1/8/2024

Page content applies to build 13.0.1.1071
