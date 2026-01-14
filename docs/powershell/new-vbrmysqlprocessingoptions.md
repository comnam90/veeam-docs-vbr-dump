---
title: "New-VBRMySQLProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmysqlprocessingoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# New-VBRMySQLProcessingOptions

In this article

Short Description

Defines settings for processing backed-up MySQL databases on Linux computers.

Applies to:

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define settings for processing MySQL database transaction logs using credentials.

|  |
| --- |
| New-VBRMySQLProcessingOptions [-Credentials <CCredentials>]  [<CommonParameters>] |

* Define settings for processing MySQL database transaction logs using the password file.

|  |
| --- |
| New-VBRMySQLProcessingOptions [-PasswordFilePath <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRMySQLProcessingOptions object. This object contains settings for processing backed-up MySQL databases for Veeam Agent backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credentials | Specifies the MySQL credentials that Veeam Agent will use to connect to the MySQL Server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| PasswordFilePath | Specifies the absolute path for the password file. Veeam Agent will use this password file to connect to the MySQL Server.  Default: /root/.my.cnf.  Note:   * Start the absolute path with the / symbol. * The cmdlet will return an error if you provide this parameter when the Credentials parameter is already specified. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRMySQLProcessingOptions object that contains settings for processing backed-up MySQL databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Settings for Processing Backed-up MySQL Database Using Credentials

|  |  |
| --- | --- |
| This example shows how to define settings for processing backed-up MySQL databases using credentials.  |  | | --- | | $creds = Get-VBRCredentials -Name \*Administrator\*  New-VBRMySQLProcessingOptions -Credentials $creds |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 2. Run the New-VBRMySQLProcessingOptions cmdlet. Set the $creds variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Settings for Processing Backed-up MySQL Database Using Password File

|  |  |
| --- | --- |
| This command defines settings for processing backed-up MySQL databases using the absolute path for the password file.  |  | | --- | | New-VBRMySQLProcessingOptions -PasswordFilePath "/root/.my.cnf." | |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
