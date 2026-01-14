---
title: "Add-VBRvCloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcloud.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Add-VBRvCloud

In this article

Short Description

Adds a Cloud Director server to Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a Cloud Director server using the user name/password scenario.

|  |
| --- |
| Add-VBRvCloud -Name <string> -User <string> -Password <string> [-Url <string>] [-Description <string>]  [<CommonParameters>] |

* Add a Cloud Director server using the credentials scenario.

|  |
| --- |
| Add-VBRvCloud -Name <string> -Credentials <CCredentials> [-Url <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a new Cloud Director server to Veeam Backup & Replication infrastructure.

|  |
| --- |
| ![Add-VBRvCloud](images/icon_note.webp) Note: |
| Run the [Add-VBRvCloudVC](add-vbrvcloudvc.md) cmdlet to add a vCenter Server managed by Cloud Director to Veeam Backup & Replication infrastructure. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the full DNS name or IP address of the Cloud Director server or any cell in the Cloud Director infrastructure. | String | True | 0 | False |
| User | Specifies the user name you want to use for authenticating with the Cloud Director server.  If you use the Username/Password scenario, the Credentials parameter must be omitted. | String | True | 1 | False |
| Password | Specifies the password you want to use for authenticating with the Cloud Director server.  If you use the Username/Password scenario, the Credentials parameter must be omitted. | String | True | 2 | False |
| Credentials | Specifies the credentials you want to use for authenticating with the Cloud Director server.  If you use the Credentials scenario, the User and Password parameters must be omitted. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Url | Specifies the URL you want to connect to the Cloud Director Web API with. | String | False | Named | False |
| Description | Specifies the description of the new Cloud Director server. If not set, the user name who created the server and the date and time of creation will be added by default. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CHost

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Cloud Director Server with User Name and Password

|  |  |
| --- | --- |
| This command creates a new vCloudDirectorServer server with the following settings:   * The URL address is https://vclouddirectorserver:443. * The user name is Administrator and the password is password. * The description is Cloud Director Server.   |  | | --- | | Add-VBRvCloud -Name "vCloudDirectorServer.domain.com" -User Administrator -Password password -Url "https://vclouddirectorserver:443" -Description "Cloud Director Server" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Cloud Director Server with Saved Credentials

|  |  |
| --- | --- |
| This example shows how to create a new vCloudDirectorServer server with the following settings:   * The URL address is https://vclouddirectorserver:443. * The user name is Administrator and the password is password. * The description is the default one.   |  | | --- | | $administrator = Get-VBRCredentials -Name "Administrator"  Add-VBRvCloud -Name "vCloudDirectorServer.domain.com" -Credentials $administrator -Url "https://vclouddirectorserver:443" |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $administrator variable. 2. Run the Add-VBRvCloud cmdlet. Specify the Name parameter value. Set the $administrator variable as the Credentials parameter value. Specify the Url parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
