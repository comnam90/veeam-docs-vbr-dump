---
title: "New-VBRMSSQLProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmssqlprocessingoptions.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---

# New-VBRMSSQLProcessingOptions


Short Description

Creates the Microsoft SQL Server database log backup settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMSSQLProcessingOptions [-EnableLogBackup] [-LogBackupPeriod <Int32>] [-EnableCopyOnlyBackup]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Microsoft SQL Server.

Use this cmdlet to create Microsoft SQL Server database log backup settings. You can set up the following options:

* Enable or disable transaction log backup.
* Set the period for transaction log backups.
* Enable or disable the copy-only log backup without interrupting the backup chain.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EnableLogBackup | Enables Microsoft SQL Server log backups when creating SQL processing options objects for application backup policies. | SwitchParameter | False | Named | False |
| LogBackupPeriod | Specifies the integer defining the frequency for logs backup in minutes.  Permitted values: 5 to 480. | Int32 | False | Named | False |
| EnableCopyOnlyBackup | Enables copy-only mode for log backups. Using this parameter can prevent backup chain disruptions. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRMSSQLProcessingOptions object that defines Microsoft SQL Server database processing settings.

Example

Create SQL Processing Options for Veeam Plug-In for Microsoft SQL Server Application Backup Policies

This example shows how to create new Microsoft SQL Server processing options for application backup policies for Veeam Plug-In for Microsoft SQL Server. The policy will enable log backup, set the log backup period to 10 minutes and enable copy-only log backup.

|  |
| --- |
| New-VBRMSSQLProcessingOptions -EnableLogBackup -LogBackupPeriod 10 -EnableCopyOnlyBackup |


