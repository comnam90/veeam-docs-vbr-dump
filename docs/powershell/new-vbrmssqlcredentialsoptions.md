---
title: "New-VBRMSSQLCredentialsOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmssqlcredentialsoptions.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# New-VBRMSSQLCredentialsOptions

In this article

Short Description

Creates Microsoft SQL Server credentials configuration that defines the connection between Veeam Backup & Replication and a discovered Microsoft SQL Server instance for Veeam Plug-In for Microsoft SQL Server backup operations.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMSSQLCredentialsOptions -Instance <VBRDiscoveredMSSQL> -Credentials <CCredentials> [-UseSAAccount]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Microsoft SQL Server.

Use this cmdlet to set authentication credentials for the Microsoft SQL Server instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Defines the discovered Microsoft SQL Server instance. | VBRDiscoveredMSSQL | True | Named | False |
| Credentials | Specifies the credentials used to connect to the Microsoft SQL Server instance. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| UseSAAccount | Applies use of Microsoft SQL Server authentication account for authentication instead of the supplied Windows OS credentials. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Example

Associate Discovered Microsoft SQL Server Instance with Specific Credentials

This example shows how to apply stored service account credentials to the discovered Microsoft SQL Server instance.

|  |
| --- |
| $creds = Get‑VBRCredentials -Name "SQL\_Account"  $sqlcredentials = New‑VBRMSSQLCredentialsOptions -Credentials $creds -Instance $mssqlInstance  $mssqlInstances = Get-VBRDiscoveredApplication -MSSQL -MSSQLEntityType -Instance  $mssqlInstance = $mssqlInstances[0] |

Perform the following steps:

1. Run the [Get‑VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable.
2. Run the New‑VBRMSSQLCredentialsOptions cmdlet. Specify the Credentials parameter with the $creds variable. Specify the Instance parameter with the name of the Microsoft SQL Server instance. Save the result to the $sqlcredentials variable.
3. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. Specify the MSSQL, MSSQLEntityType and Instance parameters. Save the result to the $mssqlInstances variable.

Page updated 12/19/2025

Page content applies to build 13.0.1.1071
