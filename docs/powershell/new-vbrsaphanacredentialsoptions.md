---
title: "New-VBRSAPHANACredentialsOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsaphanacredentialsoptions.html"
last_updated: "1/13/2025"
product_version: "13.0.1.1071"
---

# New-VBRSAPHANACredentialsOptions


Short Description

Creates the SAP HANA credentials settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSAPHANACredentialsOptions -SAPSystem <VBRDiscoveredSAPHANA> -SSHCredentials <CCredentials> -BackupCredentials <CCredentials>  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for SAP HANA.

This cmdlet creates SAP HANA credentials settings. You can set up the following options:

* The name of the SAP system.
* OS user account to run the HDBSQL command line tool.
* DB user account to perform backup and recovery operations.

|  |
| --- |
| Important |
| Keep in mind the following user account privilege requirements:   * The OS user account must have sufficient privileges to run the HDBSQL command line tool - for example, this can be the <sid>adm user. * The DB user account used to perform backup and recovery operations with system and tenant databases must have the following privileges:  * BACKUP ADMIN * CATALOG READ * DATABASE BACKUP ADMIN |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SAPSystem | Specifies the name of the SAP system. | Accepts string or the [VBRDiscoveredSAPHANA](vbrdiscoveredsaphana.md) object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | True | Named | False |
| SSHCredentials | Specifies the OS user account credentials for SAP HANA database processing. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| BackupCredentials | Specifies the DB user account credentials for SAP HANA database processing. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSAPHANACredentialsOptions object that defines SAP HANA credentials settings.

Examples

Creating SAP HANA Credentials Settings for Application Backup Policies for Veeam Plug-In for SAP HANA

This example shows how to create an SAP HANA credentials settings for application backup policies for Veeam Plug-In for SAP HANA.

|  |
| --- |
| $os\_administrator = Get-VBRCredentials  $db\_administrator = Get-VBRCredentials  New-VBRSAPHANAProcessingOptions -SAPSystem SH4 -SSHCredentials $os\_administrator -BackupCredentials $db\_administrator |

Perform the following steps:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $os\_administrator variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $db\_administrator variable.
3. Run the New-VBRSAPHANACredentialsOptions cmdlet. Specify the SAPSystem parameter value. Set the $os\_administrator as the SSHCredentials parameter value. Set the $db\_administrator variable as BackupCredentials parameter value.

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)


