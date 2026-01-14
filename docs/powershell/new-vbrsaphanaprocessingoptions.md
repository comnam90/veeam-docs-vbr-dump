---
title: "New-VBRSAPHANAProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsaphanaprocessingoptions.html"
last_updated: "12/6/2024"
product_version: "13.0.1.1071"
---

# New-VBRSAPHANAProcessingOptions

In this article

Short Description

Creates the SAP HANA database processing settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSAPHANAProcessingOptions [-RedoLogsBackupPeriod <Int32>] [-LogBackupMode <VBRSAPHANALogBackupMode>] [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for SAP HANA.

This cmdlet creates SAP HANA database processing settings. You can set up the following options:

* The way Veeam Backup & Replication will process redo logs.
* Schedule settings for redo logs processing.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RedoLogsBackupPeriod | Specifies the integer defining the frequency for redo logs backup in minutes.  Permitted values: 5 to 480. | Int32 | False | Named | False |
| LogBackupMode | Specifies the way of database processing:   * VeeamManaged: use this option if you want to perform database processing with Data Mover by Veeam Software. * SAPHANAManaged: use this option if you want to perform database processing with SAP HANA. | VBRSAPHANALogBackupMode | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSAPHANAProcessingOptions object that defines SAP HANA database processing settings.

Examples

Creating SAP HANA Database Processing Settings for Application Backup Policies for Veeam Plug-In for SAP HANA

This command creates an SAP HANA database processing settings for application backup policies for Veeam Plug-In for SAP HANA. The policy will back up redo logs every 15 minutes using SAP HANA tools.

|  |
| --- |
| New-VBRSAPHANAProcessingOptions -RedoLogsBackupPeriod 15 -LogBackupMode SAPHANAManaged |

Page updated 12/6/2024

Page content applies to build 13.0.1.1071
