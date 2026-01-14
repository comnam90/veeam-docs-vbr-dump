---
title: "Set-VBRESX (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbresx.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Set-VBRESX (obsolete)

In this article

Short Description

Modifies ESXi hosts added to Veeam Backup & Replication.

|  |
| --- |
| ![Set-VBRESX (obsolete)](images/icon_note.webp) Note: |
| This cmdlet is obsolete and will not be supported the next version. |

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRESX -Server <CHost> [-Credentials <CCredentials>] [-SSHCredentials <CCredentials>] [-SSHEnable] [-Port <int>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an ESXi host added to the Veeam Backup & Replication. To modify settings, you need to specify new values for the necessary parameters. The parameters that you omit will remain unchanged.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the ESXi host you want to modify. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Credentials | Specifies the credentials you want to use for authenticating with the ESXi server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| SSHCredentials | For SSH connection.  Specify credentials you want to use to authenticate with the service console. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| SSHEnable | For SSH connection.  Defines that the ESXi host is connected using service console connection. | SwitchParameter | False | Named | False |
| Port | Specifies the Web service port for connection to the ESXi host.  Default: 443. | Int | False | Named | False |
| Description | Specifies the description of the ESXi server. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Changing Credentials and Web Service Port Settings for ESXi Host

This example shows how to change the credentials and Web service port settings for the ESXi host.

|  |
| --- |
| $host = Get-VBRServer -Type ESXi -Name support.east.local  $creds = Get-Credential  Set-VBRESX -Server $host -Credentials $creds -Port 444 |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the ESXi option for the Type parameter value. Specify the Name parameter value. Save the result to the $host variable.
2. Run the Get-Credential cmdlet. Type the credentials you want to use for authenticating with the ESXi host. Save the result to the $creds variable.
3. Run the Set-VBRESX cmdlet. Set the $host variable as the Server parameter value. Set the $creds variable as the Credentials parameter value. Specify the Port parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
