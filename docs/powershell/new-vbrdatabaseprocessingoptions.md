---
title: "New-VBRDatabaseProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrdatabaseprocessingoptions.html"
last_updated: "10/23/2025"
product_version: "13.0.1.1071"
---

# New-VBRDatabaseProcessingOptions

In this article

Short Description

Creates the database processing settings for application backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRDatabaseProcessingOptions -BackupObject <Object> [-OracleRMANProcessingOptions <VBROracleRMANProcessingOptions>] [-SAPHANAProcessingOptions <VBRSAPHANAProcessingOptions>] [-SAPOnOracleProcessingOptions <VBRSAPOnOracleProcessingOptions>] [-MSSQLProcessingOptions <VBRMSSQLProcessingOptions>] [-PluggableDatabasesOptions <VBRPluggableDatabasesOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRDatabaseProcessingOptions object that contains database processing settings for application backup policies.

You can use this cmdlet to create a schedule for application backup policies for the following Veeam Plug-Ins managed by Veeam Backup & Replication:

* Veeam Plug-In for Oracle RMAN
* Veeam Plug-In for SAP HANA
* Veeam Plug-In for SAP on Oracle
* Veeam Plug-In for Microsoft SQL Server

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies an array of protection groups and discovered computers that you want to add to the application backup policy. | Accepts the Object object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | False |
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

Creating SAP on Oracle Database Processing Settings for Application Backup Policies for Veeam Plug-In for SAP on Oracle

This example shows how to create a SAP on Oracle database processing settings for application backup policies for Veeam Plug-In for SAP on Oracle. The policy will back up archived logs every 15 minutes and send application backups to the target storage using 3 parallel data channels.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Database Servers"  $db\_administrator = Get-VBRCredentials  $processing\_settings = New-VBRSAPOnOracleProcessingOptions -Credentials $db\_administrator -DeleteSourceLogs Keep -ArchiveLogBackupPeriod 15  New-VBRDatabaseProcessingOptions -BackupObject $group -SAPOnOracleProcessingOptions $processing\_settings |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $db\_administrator variable.
3. Run the [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md) cmdlet. Set the $db\_administrator variable as the Credentials parameter value. Specify the DeleteSourceLogs and ArchiveLogBackupPeriod parameter values. Save the result to the $processing\_settings variable.
4. Run the New-VBRDatabaseProcessingOptions cmdlet. Set the $group variable as the BackupObject parameter value. Set the $processing\_settings variable as the SAPOnOracleProcessingOptions parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBRSAPOnOracleProcessingOptions](new-vbrsaponoracleprocessingoptions.md)
* [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md)
* [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md)
* [New-VBRMSSQLProcessingOptions](new-vbrmssqlprocessingoptions.md)
* [New-VBRPluggableDatabasesOptions](new-vbrpluggabledatabasesoptions.md)

Page updated 10/23/2025

Page content applies to build 13.0.1.1071
