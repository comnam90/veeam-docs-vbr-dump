---
title: "Set-VBRNDMPServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrndmpserver.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNDMPServer

In this article

Short Description

Modifies NDMP server settings.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

|  |
| --- |
| Set-VBRNDMPServer -Server <VBRNDMPServer> [-Name <string>] [-Port <int>] [-Credentials <CCredentials>] [-GatewayMode <VBRGatewayMode> {Automatic | SelectedGateway}] [-SelectedGateway <CHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a selected NDMP server.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the NDMP server that you want to modify. | Accepts the VBRNDMPServer object. To get this object, run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. | True | Named | False |
| Name | Specifies the DNS or IP address of the NDMP server that you want to modify. | String | False | Named | False |
| Port | Specifies the port. Veeam Backup & Replication will use that port to connect to the NDMP server. | Int | False | Named | False |
| Credentials | Specifies the credentials. Veeam Backup & Replication will use these credentials to connect to the NDMP server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| GatewayMode | Specifies the gateway server. Veeam Backup & Replication will use this gateway server to connect to the NDMP server.  You can specify the following modes of selecting the gateway server:   * Automatic - use this option if you want Veeam Backup & Replication to choose the gateway server automatically. * SelectedGateway - use this option if you want to specify the particlular gateway server. Use the SelectedGateway parameter to specify the server. | VBRGatewayMode | False | Named | False |
| SelectedGateway | For specifying a particular gateway server with the SelectedGateway option.  Specifies the server that you want to use as the gateway server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNDMPServer](vbrndmpserver.md)

Examples

Changing Gateway Server Selection for NDMP Server

This command shows how to change the gateway server selection mode for an NDMP server. Veeam Backup & Replication will use a specific gateway server.

|  |
| --- |
| $ndmp = Get-VBRNDMPServer -Name "NetApp.tech.local"  $gateway = Get-VBRServer  -Name "Gateway server"  $creds = Get-VBRCredentials -Name "GatewayServer"  Set-VBRNDMPServer -Name "NetApp.tech.local" -Credentials $creds -GatewayMode SelectedGateway -SelectedGateway $gateway -Port 10000 |

Perform the following steps:

1. Run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. Specify the Name parameter value. Save the result to the $ndmp variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter. Save the result to the $gateway variable.
3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable.
4. Run the Set-VBRNDMPServer cmdlet. Specify the following settings:

* Specify the Name parameter value.

* Set the $creds variable as the Credentials parameter value.
* Set the SelectedGateway option for the GatewayMode parameter.
* Set the $gateway variable as the SelectedGateway parameter value.

* Specify the Port parameter value.

Related Commands

* [Get-VBRNDMPServer](get-vbrndmpserver.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
