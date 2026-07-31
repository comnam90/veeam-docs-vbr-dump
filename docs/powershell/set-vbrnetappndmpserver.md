---
title: "Set-VBRNetAppNDMPServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnetappndmpserver.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRNetAppNDMPServer


Short Description

Modifies a NetApp NDMP server.

Applies to

Product Edition: Enterprise

Syntax

|  |
| --- |
| Set-VBRNetAppNDMPServer -Server <VBRNetAppNDMPServer> [-Credentials <CCredentials>] [-GatewayMode <VBRGatewayMode>] [-SelectedGateway <CHost>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies the settings of a NetApp NDMP server in the Veeam Backup & Replication infrastructure. You can update the credentials and gateway server selection settings.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Server | Specifies the NetApp NDMP server that you want to modify. | Accepts the VBRNetAppNDMPServer object. To get this object, run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. | True | Named | True (ByValue) |
| Credentials | Specifies the credentials. Veeam Backup & Replication will use these credentials to connect to the NetApp NDMP server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| GatewayMode | Specifies the gateway server selection mode. Veeam Backup & Replication will use this gateway server to connect to the NDMP server.  You can specify the following modes:   * Automatic — Veeam Backup & Replication automatically selects the gateway server. * SelectedGateway — specifies a particular gateway server explicitly. Use the SelectedGateway parameter to specify the server. | VBRGatewayMode | False | Named | False |
| SelectedGateway | For the SelectedGateway option in the GatewayMode parameter.  Specifies the server that you want to use as the gateway server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNetAppNDMPServer object that contains updated information about the NetApp NDMP server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Credentials on a NetApp NDMP Server

|  |  |
| --- | --- |
| This example shows how to update the credentials on a NetApp NDMP server.  |  | | --- | | $server = Get-VBRNDMPServer -Name "172.18.12.1"  $creds = Get-VBRCredentials -Name "ndmp-new-admin"  Set-VBRNetAppNDMPServer -Server $server -Credentials $creds |  Perform the following steps:   1. Run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 3. Run the Set-VBRNetAppNDMPServer cmdlet. Set the $server variable as the Server parameter value. Set the $creds variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying the Gateway Mode on a NetApp NDMP Server

|  |  |
| --- | --- |
| This example shows how to configure a specific gateway server for a NetApp NDMP server.  |  | | --- | | $server = Get-VBRNDMPServer -Name "172.18.12.1"  $gateway = Get-VBRServer -Name "172.18.1.50"  Set-VBRNetAppNDMPServer -Server $server -GatewayMode SelectedGateway -SelectedGateway $gateway |  Perform the following steps:   1. Run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $gateway variable. 3. Run the Set-VBRNetAppNDMPServer cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Set SelectedGateway as the GatewayMode parameter value. * Set the $gateway variable as the SelectedGateway parameter value. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRNDMPServer](get-vbrndmpserver.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 2026-06-02

