---
title: "Add-VBRCloudGateway"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudgateway.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCloudGateway

In this article

Short Description

Creates cloud gateways for Veeam Cloud Connect.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Add-VBRCloudGateway [-Description <string>] [-Server <CHost>] [-IpAddress <ipaddress>] [-IncomingPort <int>] [-NATPort <int>] [-NetworkMode <VBRGatewayNetworkMode> {Direct | NAT}]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a cloud gateway.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Description | Specifies the description of the cloud gateway. | String | False | Named | False |
| Server | Specifies server that will perform the role of a cloud gateway. You can select any server added to Veeam Backup & Replication or assign the cloud gateway role to the Veeam backup server itself.  Accepted server types: Windows, Local.  Default: Local. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| IpAddress | Specifies an external IP address of the NAT or network interface gateway. | Accepts the IPAddress object or string. | False | Named | False |
| IncomingPort | Specifies a port on the NAT gateway used for listening to connections from users and passing cloud commands from users to the SP Veeam backup server.  Permitted values: 1 to 65535.  Default: 6180. | Int32 | False | Named | False |
| NATPort | Specifies an external port that will be used by the Veeam backup server to connect to the gateway.  Permitted values: 1 to 65535.  Default: (for Direct) null, (for NAT) 6180. | Int32 | False | Named | False |
| NetworkMode | Specifies the network mode: Direct, NAT. | VBRGatewayNetworkMode | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudGateway](vbrcloudgateway.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding New Gateway with Direct Network Connection

|  |  |
| --- | --- |
| This example shows how to add a new cloud gateway with a direct network connection. The port that will be used by Veeam Backup & Replication to connect to the gateway server is 6260.  |  | | --- | | $server = Get-VBRServer -Name "Cloud\_Gateway"  Add-VBRCloudGateway -Server $server -Description "Gateway directly connected to Internet" -IpAddress 104.45.85.123 -IncomingPort 6260 -NetworkMode Direct |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Run the Add-VBRCloudGateway cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Description parameter value. * Specify the IpAddress parameter value. * Specify the IncomingPort parameter value. * Set the Direct option for the NetworkMode parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding New Gateway in Local Network Behind NAT Gateway

|  |  |
| --- | --- |
| This example shows how to add a new cloud gateway in the local network behind the NAT gateway with the following settings:   * The external NAT gateway IP is 104.45.95.227. * The port that will be used by Veeam Backup & Replication to connect to the gateway server is 6180. * The port that will be used by the NAT gateway is 7180.   |  | | --- | | $server = Get-VBRServer -Name "Cloud\_Gateway"  Add-VBRCloudGateway -Server $server -Description "Gateway behind NAT" -IpAddress 104.45.95.227 -IncomingPort 6180 -NATPort 7180 -NetworkMode NAT |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Run the Add-VBRCloudGateway cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Description parameter value. * Specify the IpAddress parameter value. * Specify the IncomingPort parameter value. * Specify the NATPort parameter value. * Set the NAT option for the NetworkMode parameter. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
