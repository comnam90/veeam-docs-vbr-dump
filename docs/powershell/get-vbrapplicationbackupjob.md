---
title: "Get-VBRApplicationBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationbackupjob.html"
last_updated: "10/22/2025"
product_version: "13.0.1.1071"
---

# Get-VBRApplicationBackupJob


Short Description

Returns application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRApplicationBackupJob [-Id <guid[]>] [-Name <string[]>] [-Type {OracleRMAN | SAPHANA | SAPOnOracle}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of application backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an ID of an application backup policy. | Guid[] | False | Named | False |
| Name | Specifies a name of an application backup policy. | String[] | False | Named | False |
| Type | Specifies the type of Veeam Plug-In to be installed on the protected computers:   * OracleRMAN: for Veeam Plug-In for Oracle RMAN * SAPHANA: for Veeam Plug-In for SAP HANA * SAPOnOracle: for Veeam Plug-In for SAP on Oracle * MongoDB: for MongoDB Backup * MSSQL: for Veeam Plug-In for Microsoft SQL Server   The cmdlet will return application backup policies with applications of these types. | VBRApplicationType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRApplicationBackupJob[] object that contains settings of application backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Application Backup Policies

|  |  |
| --- | --- |
| This command returns an array of all application backup policies that are added to Veeam Backup & Replication.  |  | | --- | | Get-VBRApplicationBackupJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specified Application Backup Job by Name

|  |  |
| --- | --- |
| This command returns the Plugin Policy 05 application backup policy.  |  | | --- | | Get-VBRApplicationBackupJob -Name "Plugin Policy 05" | |


