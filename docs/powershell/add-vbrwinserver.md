---
title: "Add-VBRWinServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrwinserver.html"
last_updated: "7/22/2025"
product_version: "13.0.1.1071"
---

# Add-VBRWinServer

In this article

Short Description

Adds a Windows server to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a Windows server using an account user name and a password.

|  |
| --- |
| Add-VBRWinServer -Name <String> -User <String> -Password <String> [-Description <String>]  [<CommonParameters>] |

* Add a Windows server using credentials managed by Veeam Backup & Replication.

|  |
| --- |
| Add-VBRWinServer -Name <String> [-Description <String>] -Credentials <CCredentials>  [<CommonParameters>] |

* Add a Windows server using credentials using certificate-based authentication.

|  |
| --- |
| Add-VBRWinServer -Name <String> [-Description <String>] -UseCertificate  [<CommonParameters>] |

Detailed Description

This cmdlet adds a Windows server to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the DNS name of the Windows server. | String | True | Named | False |
| User | Specifies the user name you want to use for authenticating with the Windows server. | String | True | Named | False |
| Password | Specifies the password you want to use for authenticating with the Windows server. | String | True | Named | False |
| Description | Specifies the description of the Windows server. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the Windows server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| UseCertificate | Defines that the cmdlet will use certificate-based authentication to authenticate with the Windows server.  This authentication method requires Veeam Deployment Kit pre-installed on the target Windows server. | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of a Windows server added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding New Windows Server Using User Name and Password

|  |  |
| --- | --- |
| This command adds a new Windows server named WinServer with the Administrator user name and the qwerty password of the account. The description is Windows File Server.  |  | | --- | | Add-VBRWinServer -Name "WinServer" -User "Administrator" -Password "qwerty" -Description "Windows File Server" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding New Windows Server Using Credentials

|  |  |
| --- | --- |
| This example shows how to add a new Windows server named WinServer using credentials. The description is Windows File Server.  |  | | --- | | $Administrator = Get-VBRCredentials  Add-VBRWinServer -Name "WinServer" -Credentials $Administrator -Description "Windows File Server" |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $Administrator variable. 2. Run the Add-VBRWinServer cmdlet. Specify the Name parameter value. Set the $Administrator variable as the Credentials parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding New Windows Server Using Certificate-Based Authentication

|  |  |
| --- | --- |
| This example shows how to add a new Windows server named WinServer using a certificate. The description is Windows File Server.  |  | | --- | | Add-VBRWinServer -Name "WinServer" -Description "Windows File Server" -UseCertificate |  Perform the following steps:   1. Install Veeam Deployment Kit on the target Windows server. 2. Run the Add-VBRWinServer cmdlet. Specify the Name and the Description parameter values. Provide the UseCertificate parameter. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 7/22/2025

Page content applies to build 13.0.1.1071
