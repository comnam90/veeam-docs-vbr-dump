---
title: "Set-VBRSAPOnOracleProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsaponoracleprocessingoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSAPOnOracleProcessingOptions

In this article

Short Description

Modifies the SAP on Oracle database processing settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBROracleRMANProcessingOptions -Options -Credentials <CCredentials> [-DeleteSourceLogs] [-ArchiveLogBackupPeriod <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for SAP on Oracle.

This cmdlet modifies SAP on Oracle database processing settings. You can set up the following options:

* The way Veeam Backup & Replication will process archived logs.
* Schedule settings for archived logs processing.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the database processing options that you plan to modify. | Accepts the VBRSAPOnOracleProcessingOptions object. To get this object, run the [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| Credentials | Specifies the credentials for SAP on Oracle database processing. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| DeleteSourceLogs | Defines that Veeam Plug-In should delete archived logs that were backed up. | SwitchParameter | False | Named | False |
| ArchiveLogBackupPeriod | Specifies the integer defining the frequency for archived logs backup in minutes.  Permitted values: 5 to 480. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSAPOnOracleProcessingOptions object that defines SAP on Oracle database processing settings.

Examples

Creating and Modifying SAP on Oracle Database Processing Settings for Application Backup Policies for Veeam Plug-In for SAP on Oracle

This example shows how to create and modify a SAP on Oracle backup settings for application backup policies for Veeam Plug-In for SAP on Oracle. The modified policy will back up archived logs every 30 minutes.

|  |
| --- |
| $db\_administrator = Get-VBRCredentials  $processoptions = New-VBRSAPOnOracleProcessingOptions -Credentials $db\_administrator -DeleteSourceLogs -ArchiveLogBackupPeriod 15 -ParallelChannelsCount 1  Set-VBRSAPOnOracleProcessingOptions -Options $processoptions -Credentials $db\_administrator -DeleteSourceLogs -ArchiveLogBackupPeriod 30 |

Perform the following steps:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $db\_administrator variable.
2. Run the [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md) cmdlet. Specify the Credentials, DeleteSourceLogs, ArchiveLogBackupPeriod and ParallelChannelsCount parameter values. Save the result to the $processoptions variable.
3. Run the Set-VBRSAPOnOracleProcessingOptions cmdlet. Specify the following settings:

* Set the $processoptions variable as the Options parameter value.
* Set the $db\_administrator variable as the Credentials parameter value.
* Provide the DeleteSourceLogs parameter.
* Specify the ArchiveLogBackupPeriod parameter value.

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
