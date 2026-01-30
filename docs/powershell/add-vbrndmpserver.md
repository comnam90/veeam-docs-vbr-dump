---
title: "Add-VBRNDMPServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrndmpserver.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Add-VBRNDMPServer


Short Description

Adds NDMP servers to the backup infrastructure.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

|  |
| --- |
| Add-VBRNDMPServer -Name <string> -Port <int> -Credentials <CCredentials> -GatewayMode <VBRGatewayMode> {Automatic | SelectedGateway} [-SelectedGateway <CHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds NDMP servers to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the DNS or IP of an NDMP server that you want to add to Veeam Backup & Replication. | String | True | Named | False |
| Port | Specifies the port. Veeam Backup & Replication will use that port to connect to an NDMP server. | Int | True | Named | False |
| Credentials | Specifies the credentials. Veeam Backup & Replication will use these credentials to connect to an NDMP server. | Accepts the CCredentials object. To get this object, run [Add-VBRCredentials](add-vbrcredentials.md) cmdlet. | True | Named | False |
| GatewayMode | Specifies a gateway server. Veeam Backup & Replication will use this gateway server to connect to the NDMP server.  You can select the following modes of selecting the gateway server:   * Automatic - use this option if you want Veeam Backup & Replication to choose the gateway server automatically. * SelectedGateway - use this option if you want to specify the gateway server explicitly. Use the SelectedGateway parameter to specify the gateway server. | VBRGatewayMode | True | Named | False |
| SelectedGateway | For specifying a gateway server explicitly with the SelectedGateway option.  Specifies the server that you want to use as the gateway server. | Accepts the CHost object. To get this object, run [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNDMPServer](vbrndmpserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding NDMP Server with Automatic Gateway Selection

|  |  |
| --- | --- |
| This example shows how to add an NDMP server to the backup infrastructure. Veeam Backup & Replication will select the gateway server automatically.  |  | | --- | | $creds = Add-VBRCredentials -User "New NDMP" -Password "Password"  Add-VBRNDMPServer -Name "NetApp.tech.local" -Credentials $creds -GatewayMode Automatic -Port 10000 |  Perform the following steps:   1. Run the [Add-VBRCredentials](add-vbrcredentials.md) cmdlet. Specify the User and the Password parameters value. Save the result to the $creds variable. 2. Run the Add-VBRNDMPServer cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $creds variable as the Credentials parameter value. * Set the Automatic option for the GatewayMode parameter. * Specify the Port parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding NDMP Server with Manual Gateway Selection

|  |  |
| --- | --- |
| This example shows how to add an NDMP server to the backup infrastructure. Veeam Backup & Replication will use selected server as the gateway server.  |  | | --- | | $creds = Add-VBRCredentials -User "New NDMP" -Password "Password"  $gateway = Get-VBRServer  -Name "Gateway server"  Add-VBRNDMPServer -Name "NDMPv4 Storage" -Port 1000 -Credentials $creds -GatewayMode SelectedGateway -SelectedGateway $gateway |  Perform the following steps:   1. Run the [Add-VBRCredentials](add-vbrcredentials.md) cmdlet. Specify the User and the Password parameters value. Save the result to the $creds variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter. Save the result to the $gateway variable. 3. Run the Add-VBRNDMPServer cmdlet. Specify the following settings:  * Specify the Name parameter value. * Specify the Port parameter value.  * Set the $creds variable as the Credentials parameter value. * Set the SelectedGateway option for the GatewayMode parameter. * Set the $gateway variable as the SelectedGateway parameter value. |

Related Commands

* [Add-VBRCredentials](add-vbrcredentials.md)
* [Get-VBRServer](get-vbrserver.md)


