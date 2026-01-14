---
title: "Set-VBRSAPHANAProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsaphanaprocessingoptions.html"
last_updated: "12/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSAPHANAProcessingOptions

In this article

Short Description

Modifies the SAP HANA database processing settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSAPHANAProcessingOptions -Options <VBRSAPHANAProcessingOptions> [-RedoLogBackupPeriod <int>] [-LogBackupMode {VeeamManaged | SAPHANAManaged}]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for SAP HANA.

This cmdlet modifies SAP HANA database processing settings. You can modify the following options:

* The way Veeam Backup & Replication will process redo logs.
* Schedule settings for redo logs processing.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the database processing options that you plan to modify. | Accepts the VBRSAPHANAProcessingOptions object. To get this object, run the [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| RedoLogsBackupPeriod | Specifies the integer defining the frequency for redo logs backup in minutes.  Permitted values: 5 to 480. | Int32 | False | Named | False |
| LogBackupMode | Specifies the way of database processing:   * VeeamManaged: use this option if you want to perform database processing with Data Mover by Veeam Software. * SAPHANAManaged: use this option if you want to perform database processing with SAP HANA. | VBRSAPHANALogBackupMode | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSAPHANAProcessingOptions object that defines SAP HANA database processing settings.

Examples

Creating and Modifying SAP HANA Database Processing Settings for Application Backup Policies for Veeam Plug-In for SAP HANA

This example shows how to create and modify SAP HANA database processing settings for application backup policies for Veeam Plug-In for SAP HANA. The modified policy will back up redo logs every 30 minutes.

|  |
| --- |
| $processoptions = New-VBRSAPHANAProcessingOptions -RedoLogsBackupPeriod 15 -LogBackupMode VeeamManaged  Set-VBRSAPHANAProcessingOptions -Options $processoptions |

Perform the following steps:

1. Run the [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md) cmdlet. Specify the RedoLogsBackupPeriod and LogBackupMode parameter values. Save the result to the $processoptions variable.
2. Run the Set-VBRSAPHANAProcessingOptions cmdlet. Set the $processoptions variable as the Options parameter value. Specify the RedoLogsBackupPeriod parameter value.

Related Commands

[New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md)

Page updated 12/6/2024

Page content applies to build 13.0.1.1071
