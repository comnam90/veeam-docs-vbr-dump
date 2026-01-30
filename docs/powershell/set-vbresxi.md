---
title: "Set-VBRESXi"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbresxi.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# Set-VBRESXi


Short Description

Modifies VMware ESXi hosts added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRESXi -Server <CHost> [-Port <Int32>] [-Credentials <CCredentials>] [-Description <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an VMware ESXi host added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the ESXi host you want to modify. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Credentials | Specifies the credentials you want to use for authenticating with the ESXi server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Port | Specifies the Web service port for connection to the ESXi host.  Default: 443. | Int32 | False | Named | False |
| Description | Specifies the description of the ESXi server. | String | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will modify settings of VMware ESXi hosts without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of the VMware ESXi hosts added to the backup infrastructure.

Examples

Modifying Credentials and Port Setting of VMware ESXi Host

This example shows how to change the credentials and Web service port settings of the ESXi host.

|  |
| --- |
| $host = Get-VBRServer -Type ESXi -Name support.north.local  $creds = Get-VBRCredentials  Set-VBRESXi -Server $host -Credentials $creds -Port 442 |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $host variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable.
3. Run the Set-VBRESXi cmdlet. Set the $host variable as the Server parameter value. Set the $creds variable as the Credentials parameter value. Specify the Port parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRCredentials](get-vbrcredentials.md)


