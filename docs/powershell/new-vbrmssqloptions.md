---
title: "New-VBRMSSQLOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmssqloptions.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# New-VBRMSSQLOptions

In this article

Short Description

Creates a new Microsoft SQL Server backup options object that defines how Microsoft SQL Server transaction logs and databases are handled during backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMSSQLOptions [-ParallelChannelsCount <Int32>] [-LogBackupChannelsCount <Int32>] [-EnableCopyOnlyBackup] [-EnableDifferentialBackups] [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Microsoft SQL Server.

Use this cmdlet to configure Microsoft SQL Server specific parameters and apply them to a backup job or database object.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ParallelChannelsCount | Specifies the number of parallel data channels that Veeam Backup & Replication uses to back up a Microsoft SQL Server database. Increasing the number of channels may increase the load on the Microsoft SQL Server and backup repository.  Permitted values: 1 to 64. | Int32 | False | Named | False |
| LogBackupChannelsCount | Defines the number of parallel channels used for transaction log backups.  Permitted values: 1 to 64. | Int32 | False | Named | False |
| EnableCopyOnlyBackup | Enables copy-only mode for backups. Using this parameter can prevent backup chain disruptions.  Note: You cannot use this parameter together with the EnableDifferentialBackups parameter. | SwitchParameter | False | Named | False |
| EnableDifferentialBackups | Enables the creation of differential backups, in addition to full and transaction log backups.  Note: You cannot use this parameter together with the EnableCopyOnlyBackup parameter. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the MSSQLOptions object that defines Microsoft SQL Server backup settings.

Example

Create SQL Backup Settings for Application Backup Policies for Veeam Plug-In for Microsoft SQL Server

This example shows how to create Microsoft SQL Server backup settings for application backup policies for Veeam Plug-In for Microsoft SQL Server. The policy will send application backups to the target storage using 4 parallel data channels, send transaction log backups using 2 parallel channels and enable copy-only backup mode.

|  |
| --- |
| New-VBRMSSQLOptions -ParallelChannelsCount 4 -LogBackupChannelsCount 2 -EnableCopyOnlyBackup |

Page updated 12/19/2025

Page content applies to build 13.0.1.1071
