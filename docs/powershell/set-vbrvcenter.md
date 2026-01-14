---
title: "Set-VBRvCenter"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcenter.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRvCenter

In this article

Short Description

Modifies VMware vSphere servers added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRvCenter -Server <CHost> [-Port <int>] [-Description <string>] [-Credentials <CCredentials>] [-WhatIf] [-Confirm] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a selected VMware vCenter server added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the vCenter server you want to modify. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Port | Specifies the Web service port for connection to the vCenter server.  Default: 443. | Int | False | Named | False |
| Description | Specifies the description of the vCenter server. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the vCenter server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will modify a vCenter Server without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Modifying vCenter Server Port and Credentials

This example shows how to change the credentials and Web service port settings for the vCenter Server.

|  |
| --- |
| $server = Get-VBRServer -Type VC -Name abc.support.main.local  $creds = Get-VBRCredentials -Name "Administrator"  Set-VBRvCenter -Server $server -Credentials $creds -Port 444 |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable.
3. Run the Set-VBRvCenter cmdlet. Specify the following settings:

* Set the $server variable as the Server parameter value.
* Set the $creds variable as the Credentials parameter value.
* Specify the Port parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
