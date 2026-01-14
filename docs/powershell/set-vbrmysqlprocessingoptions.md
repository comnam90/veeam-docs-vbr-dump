---
title: "Set-VBRMySQLProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrmysqlprocessingoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRMySQLProcessingOptions

In this article

Short Description

Modifies settings for processing backed-up MySQL databases for Veeam Agent backup jobs.

Applies to:

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify settings for processing backed-up MySQL database using credentials.

|  |
| --- |
| Set-VBRMySQLProcessingOptions -Options <VBRMySQLProcessingOptions> [-Credentials <CCredentials>]  [<CommonParameters>] |

* Modify settings for processing backed-up MySQL database using the password file.

|  |
| --- |
| Set-VBRMySQLProcessingOptions -Options <VBRMySQLProcessingOptions> [-PasswordFilePath <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for processing backed-up MySQL databases for Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies settings for backed-up MySQL database. The cmdlet will modify these settings. | Accepts the VBRMySQLProcessingOptions object. To create this object, run the [New-VBRMySQLProcessingOptions](new-vbrmysqlprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| Credentials | Specifies the MySQL credentials that Veeam Agent will use to connect to the MySQL Server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| PasswordFilePath | Specifies the absolute path for the password file. Veeam Agent will use this password file to connect to the MySQL Server.  Default: "/root/.my.cnf"  Note:   * Start the absolute path with the / symbol. * The cmdlet will return an error if you provide this parameter when the Credentials parameter is already specified. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRMySQLProcessingOptions object that contains settings for processing backed-up MySQL databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Credentials for MySQL Database Processing Settings

|  |  |
| --- | --- |
| This example shows how to modify credentials for MySQL database processing settings.  |  | | --- | | $options = New-VBRMySQLProcessingOptions  $creds = Get-VBRCredentials  Set-VBRMySQLProcessingOptions -Options $options -Credentials $creds |  Perform the following steps:   1. Run the [New-VBRMySQLProcessingOptions](new-vbrmysqlprocessingoptions.md) cmdlet. Save the result to the $options variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable. 3. Run the Set-VBRMySQLProcessingOptions cmdlet. Set the $options variable as the Options parameter value. Set the $creds variable as the Credentials parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Absolute Path of Password File for MySQL Database Processing Settings

|  |  |
| --- | --- |
| This example shows how to modify absolute path of a password file for MySQL database processing settings.  |  | | --- | | $options = New-VBRMySQLProcessingOptions  Set-VBRMySQLProcessingOptions -Options $options -PasswordFilePath "/home/mydir/.my.cnf" |  Perform the following steps:   1. Run the [New-VBRMySQLProcessingOptions](new-vbrmysqlprocessingoptions.md) cmdlet. Save the result to the $options variable. 2. Run the Set-VBRMySQLProcessingOptions cmdlet. Set the $options variable as the Options parameter value. Specify the PasswordFilePath parameter value. |

Related Commands

* [New-VBRMySQLProcessingOptions](new-vbrmysqlprocessingoptions.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
