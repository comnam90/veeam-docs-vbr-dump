---
title: "Set-VBRCloudGateway"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudgateway.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudGateway

In this article

Short Description

Modifies cloud gateways.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Set-VBRCloudGateway -CloudGateway <VBRCloudGateway> [-Description <String>] [-IpAddress <String>] [-IncomingPort <Int32>] [-NATPort <Int32>] [-PassThru] [-NetworkMode <VBRGatewayNetworkMode>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an existing cloud gateway.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudGateway | Specifies the cloud gateway you want to modify. | Accepts the [VBRCloudGateway](vbrcloudgateway.md) object. To get this object, run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies the description of the cloud gateway. | String | False | Named | False |
| IpAddress | Specifies an external IP address of the NAT or network interface gateway. | Accepts IPAddress or string. | False | Named | False |
| IncomingPort | Specifies a port on the NAT gateway used for listening to connections from users and passing cloud commands from users to the SP Veeam backup server.  Permitted values: 1 to 65535.  Default: 6180. | Int32 | False | Named | False |
| NATPort | Specifies an external port that will be used by the Veeam backup server to connect to the gateway.  Permitted values: 1 to 65535.  Default: (for Direct) null, (for NAT) 6180. | Int32 | False | Named | False |
| NetworkMode | Specifies network mode: Direct, NAT. | VBRGatewayNetworkMode | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudGateway](vbrcloudgateway.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting New Port for Cloud Gateway [Using Variable]

|  |  |
| --- | --- |
| This example shows how to set a new port for the cloud gateway to connect to Veeam Backup & Replication. The new port number is set to 9012.  |  | | --- | | $cloudgateway = Get-VBRCloudGateway -Name "Cloud Gateway"  Set-VBRCloudGateway -CloudGateway $cloudgateway -IncomingPort 9012 |  Perform the following steps:   1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudgateway variable. 2. Run the Set-VBRCloudGateway cmdlet. Set the $cloudgateway variable as the CloudGateway parameter value. Specify the IncomingPort parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting New Port for Cloud Gateway [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set a new cloud gateway IP address and port to connect to Veeam Backup & Replication. The IP address is set to 172.16.10.20 and the port is set to 8062.  |  | | --- | | Get-VBRCloudGateway | Set-VBRCloudGateway -IpAddress 172.16.10.20 -IncomingPort 8062 |  Perform the following steps:   1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. 2. Pipe the cmdlet output to the Set-VBRCloudGateway cmdlet. Specify the IpAddress and the IncomingPort parameter values. |

Related Commands

[Get-VBRCloudGateway](get-vbrcloudgateway.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
