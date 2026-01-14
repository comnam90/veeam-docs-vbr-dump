---
title: "Set-VBRWinServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrwinserver.html"
last_updated: "7/22/2025"
product_version: "13.0.1.1071"
---

# Set-VBRWinServer

In this article

Short Description

Modifies Windows server added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify Windows server credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Set-VBRWinServer -Server <CHost> [-Credentials <CCredentials>] [-Description <String>]  [<CommonParameters>] |

* Modify an account user name and a password of a Windows server added to the backup infrastructure.

|  |
| --- |
| Set-VBRWinServer -Server <CHost> [-Description <String>] [-Password <String>] [-User <String>]  [<CommonParameters>] |

* Modify authentication method of a Windows server to the certificate-based authentication.

|  |
| --- |
| Set-VBRWinServer -Server <CHost> [-Description <String>] [-UseCertificate]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a Windows server added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the Windows server which settings you want to modify. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| User | Specifies a user name you want to use for authenticating with the Windows server. | String | False | Named | False |
| Password | Specifies the password you want to use for authenticating with the Windows server. | String | False | Named | False |
| Description | Specifies a description of the Windows server. | String | False | Named | False |
| Credentials | Specifies credentials you want to use for authenticating with the Windows server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| UseCertificate | Defines that the cmdlet will use certificate-based authentication to authenticate with the Windows server.  This authentication method requires Veeam Deployment Kit pre-installed on the target Windows server. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of a Windows server added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Credentials of Windows Server

|  |  |
| --- | --- |
| This example shows how to modify credentials of the WinServer07 Windows server.  |  | | --- | | $Administrator = Get-VBRCredentials  $server = Get-VBRServer -Name "WinServer07"  Set-VBRWinServer -Server $server -Credentials $Administrator -Description "Windows File Server 07" |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the Set-VBRWinServer cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Set the $Administrator variable as the Credentials parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying User Name and Password of Windows Server

|  |  |
| --- | --- |
| This example shows how to modify user name and password of the Windows server.  |  | | --- | | $server = Get-VBRServer -Name "WinServer07"  Set-VBRWinServer -Server $server -User "Administrator02" -Password "XXXXXXXX" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Set-VBRWinServer cmdlet. Set the $server variable as the Server parameter value. Specify the User parameter value. Specify the Password parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Authentication Method of Windows Server to Certificate-Based Authentication

|  |  |
| --- | --- |
| This example shows how to switch the authentication method of the WinServer07 Windows server to certificate-based authentication.  |  | | --- | | $server = Get-VBRServer -Name "WinServer07"  Set-VBRWinServer -Server $server -UseCertificate |  Perform the following steps:   1. Install Veeam Deployment Kit on the Windows server you want to modify. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the Set-VBRWinServer cmdlet. Set the $server variable as the Server parameter value. Provide the UseCertificate parameter. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 7/22/2025

Page content applies to build 13.0.1.1071
