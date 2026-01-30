---
title: "Set-VBRMSSQLProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrmssqlprocessingoptions.html"
last_updated: "10/22/2025"
product_version: "13.0.1.1071"
---

# Set-VBRMSSQLProcessingOptions


Short Description

Modifies the Microsoft SQL Server database processing settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRMSSQLProcessingOptions -Options <VBRMSSQLProcessingOptions> [-EnableLogBackup] [-LogBackupPeriod <Int32>] [-EnableCopyOnlyBackup]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Microsoft SQL Server.

Use this cmdlet to modify Microsoft SQL Server database processing settings. You can modify the following options:

* Enable or disable transaction log backup.
* Modify the period for transaction log backups.
* Enable or disable the copy-only backup without interrupting the backup chain.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the database processing options that you plan to modify. | Accepts the VBRMSSQLProcessingOptions object. To get this object, run the [New-VBRMSSQLProcessingOptions](new-vbrmssqlprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| EnableLogBackup | Enables Microsoft SQL Server log backups when creating SQL processing options objects for application backup policies. | SwitchParameter | False | Named | False |
| LogBackupPeriod | Modifies the integer defining the frequency for logs backup in minutes.  Permitted values: 5 to 480. | Int32 | False | Named | False |
| EnableCopyOnlyBackup | Enables copy-only mode for backups. Using this parameter can prevent backup chain disruptions. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Example

Modify SQL Processing Options for Veeam Plug-In for Microsoft SQL Server Application Backup Policies

This example shows how to modify existing Microsoft SQL Server processing options for application backup policies for Veeam Plug-In for Microsoft SQL Server.

|  |
| --- |
| $sqloptions = New‑VBRMSSQLProcessingOptions -EnableLogBackup -LogBackupPeriod 30 -EnableCopyOnlyBackup  Set‑VBRMSSQLProcessingOptions -Options $sqloptions |

Perform the following steps:

1. Run the [New‑VBRMSSQLProcessingOptions](new-vbrmssqlprocessingoptions.md) cmdlet. Specify the following settings:

1. Provide the EnableLogBackup parameter.
2. Specify the LogBackupPeriod parameter with the number of minutes.
3. Provide the EnableCopyOnlyBackup parameter.
4. Save the result to the $sqloptions variable.

1. Run the Set‑VBRMSSQLProcessingOptions cmdlet. Specify the Options parameter with the $sqloptions variable.


