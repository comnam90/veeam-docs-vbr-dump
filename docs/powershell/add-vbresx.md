---
title: "Add-VBRESX (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbresx.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Add-VBRESX (obsolete)

In this article

Short Description

Adds ESXi hosts to Veeam Backup & Replication.

|  |
| --- |
| ![Add-VBRESX (obsolete)](images/icon_note.webp) Note: |
| This cmdlet is obsolete and will not be supported in the next version. |

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides 2 parameter sets.

* For authenticating with user name/password:

|  |
| --- |
| Add-VBRESX -Name <string> -User <string> -Password <string> [-Port <int>] [-SSHUser <string>] [-SSHPassword <string>] [-SSHPort <int>] [-SSHEnable] [-Description <string>] [-SSHCredentials <CCredentials>]  [<CommonParameters>] |

* For authenticating with credentials:

|  |
| --- |
| Add-VBRESX -Name <string> -Credentials <CCredentials> [-Port <int>] [-SSHUser <string>] [-SSHPassword <string>] [-SSHPort <int>] [-SSHEnable] [-Description <string>] [-SSHCredentials <CCredentials>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds ESXi servers to the Veeam Backup & Replication managing console.

If an ESXi host is a part of a vCenter Server, it is recommended to add the vCenter Server instead of a single ESXi host.

When adding a new ESXi server, you will need to provide either a user name and password or credentials. Use an appropriate parameter set for each case.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the full DNS name or IP address of the ESXi host. | String | True | 1 | False |
| User | Specifies the user name you want to use for authenticating with the ESXi host. | String | True | 2 | False |
| Password | Specifies the password you want to use for authenticating with the ESXi host. | String | True | 3 | False |
| Credentials | Specifies the credentials you want to use for authenticating with the ESXi server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| Port | Specifies the Web service port for connection to the ESXi host.  Default: 443. | Int | False | Named | False |
| SSHUser | Specifies the user name of the account used for service console connection to the host (recommended). | String | False | Named | False |
| SSHPassword | Specifies the password of the account used for service console connection to the host (recommended). | String | False | Named | False |
| SSHPort | Specifies the service console port (recommended). | Int | False | Named | False |
| SSHEnable | For SSH connection.  Defines that the ESXi host is connected using service console connection. | SwitchParameter | False | Named | False |
| Description | Specifies the description of the ESXi server. | String | False | Named | False |
| SSHCredentials | For SSH connection.  Specify credentials you want to use to authenticate with the service console. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding ESXi Host with User Name and Password

|  |  |
| --- | --- |
| This command adds the ESXi host with the 172.16.11.188 IP address. The user name is root and the password is qwerty.  |  | | --- | | Add-VBRESX –Name 172.16.11.188 –User root –Password qwerty | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding ESXi Host with User Name and Password

|  |  |
| --- | --- |
| This example shows how to add the ESXi host with the 172.16.11.188 IP address and authenticates with credentials.  |  | | --- | | $Administrator = Get-VBRCredentials -Name \*Administrator\*  Add-VBRESX –Name 172.16.11.188 -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $Administrator variable. 2. Run the Add-VBRESX cmdlet. Specify the Name parameter value. Set the $Administrator variable as the Credentials parameter value. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRServer](get-vbrserver.md)
* [Remove-VBRServer](remove-vbrserver.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
