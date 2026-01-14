---
title: "Set-VBRDatabaseProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrdatabaseprocessingoptions.html"
last_updated: "10/23/2025"
product_version: "13.0.1.1071"
---

# Set-VBRDatabaseProcessingOptions

In this article

Short Description

Modifies the database processing settings for application backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRDatabaseProcessingOptions [-BackupObject <Object>] -OracleRMANProcessingOptions <VBROracleRMANProcessingOptions> [-SAPHANAProcessingOptions <VBRSAPHANAProcessingOptions>] [-SAPOnOracleProcessingOptions <VBRSAPOnOracleProcessingOptions>] [-MSSQLProcessingOptions <VBRMSSQLProcessingOptions>] [-PluggableDatabasesOptions <VBRPluggableDatabasesOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRDatabaseProcessingOptions object that contains database processing settings for application backup policies.

You can use this cmdlet to create a schedule for application backup policies for the following Veeam Plug-Ins managed by Veeam Backup & Replication:

* Veeam Plug-In for Oracle RMAN
* Veeam Plug-In for SAP HANA
* Veeam Plug-In for SAP on Oracle
* Veeam Plug-In for Microsoft SQL Server

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the database processing options that you plan to modify. | Accepts the VBRSAPOnOracleProcessingOptions object. To get this object, run the [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| BackupObject | Specifies an array of protection groups and discovered computers that you want to add to the application backup policy. | Accepts the Object object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | False | Named | False |
| OracleRMANProcessingOptions | For Veeam Plug-In for Oracle RMAN.  Specifies the Oracle RMAN database processing settings. | Accepts the VBROracleRMANProcessingOptions type. To get this object, run the [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md) cmdlet. | False | Named | False |
| SAPHANAProcessingOptions | For Veeam Plug-In for SAP HANA.  Specifies the SAP HANA database processing settings. | Accepts the VBRSAPHANAProcessingOptions object. To get this object, run the [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md) cmdlet. | False | Named | False |
| SAPOnOracleProcessingOptions | For Veeam Plug-In for SAP on Oracle.  Specifies the SAP on Oracle database processing settings. | Accepts the VBRSAPOnOracleProcessingOptions type. To get this object, run the [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md) cmdlet. | False | Named | False |
| MSSQLProcessingOptions | For Veeam Plug-In for Microsoft SQL Server.  Specifies the Microsoft SQL Server database processing settings. | Accepts the VBRMSSQLProcessingOptions type. To get this object, run the [New-VBRMSSQLProcessingOptions](new-vbrmssqlprocessingoptions.md) cmdlet. | False | Named | False |
| PluggableDatabasesOptions | For Veeam Plug-In for Oracle RMAN.  Specifies the settings for pluggable databases. | Accepts the VBRPluggableDatabasesOptions object. To get this object, run the [New-VBRPluggableDatabasesOptions](new-vbrpluggabledatabasesoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRDatabaseProcessingOptions object that contains the database processing settings for application backup policies.

Examples

Creating and Modifying SAP on Oracle Database Processing Settings for Application Backup Policies for Veeam Plug-In for SAP on Oracle

This example shows how to create a SAP on Oracle database processing settings for application backup policies for Veeam Plug-In for SAP on Oracle and modify the backup object.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Database Servers"  $db\_administrator = Get-VBRCredentials  $processing\_settings = New-VBRSAPOnOracleProcessingOptions -Credentials $db\_administrator -DeleteSourceLogs Keep -ArchiveLogBackupPeriod 15  $options = New-VBRDatabaseProcessingOptions -BackupObject $group -SAPOnOracleProcessingOptions $processing\_settings  $updated\_group = Get-VBRProtectionGroup -Name "SAP on Oracle Servers"  Set-VBRDatabaseProcessingOptions -Options $options -BackupObject $updated\_group |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $db\_administrator variable.
3. Run the [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md) cmdlet. Set the $db\_administrator variable as the Credentials parameter value. Specify the DeleteSourceLogs and ArchiveLogBackupPeriod parameter values. Save the result to the $processing\_settings variable.
4. Run the [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md) cmdlet. Set the $group as the BackupObject parameter value. Set the $processing\_settings variable as the SAPOnOracleProcessingOptions parameter value. Save the result to the $options variable.
5. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $updated\_group variable.
6. Run the Set-VBRDatabaseProcessingOptions cmdlet. Set the $options variable as the Options parameter value. Set the $updated\_group variable as the BackupObject parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md)
* [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md)
* [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md)
* [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md)
* [New-VBRMSSQLProcessingOptions](new-vbrmssqlprocessingoptions.md)

Page updated 10/23/2025

Page content applies to build 13.0.1.1071
