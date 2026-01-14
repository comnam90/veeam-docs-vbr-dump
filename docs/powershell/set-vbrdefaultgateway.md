---
title: "Set-VBRDefaultGateway"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrdefaultgateway.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRDefaultGateway

In this article

Short Description

Modifies cloud default gateways.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRDefaultGateway -Gateway <VBRDefaultGateway> [-IpAddress <String>] [-NetworkMask <String>] [-Ipv6Address <String>] [-Ipv6SubnetAddress <String>] [-Ipv6PrefixLength <Byte>] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the default cloud gateway.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Gateway | Specifies the default cloud gateway you want to modify. | Accepts the [VBRDefaultGateway](vbrdefaultgateway.md) object. To get this object, run the [Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md) cmdlet. | True | Named | True (ByValue, |
| IpAddress | Specifies the IP address you want to assign to the default gateway. | String | False | Named | False |
| NetworkMask | Specifies the network mask you want to assign to the default gateway. | String | False | Named | False |
| Ipv6Address | Specifies the IPv6 address that you want to assign to the default gateway. | String | False | Named | False |
| Ipv6SubnetAddress | Specifies the production IPv6 network. | String | False | Named | False |
| Ipv6PrefixLength | Specifies the length of an IPv6 prefix. | Byte | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDefaultGateway](vbrdefaultgateway.md)

Examples

Setting IP Address and Network Mask for Selected Default Gateway

This example shows how to set the IP address and the network mask for the selected default gateway.

|  |
| --- |
| $config = Get-VBRDefaultGatewayConfiguration  $alldefaultgateways = $config.Defaultgateway.name  $alldefaultgateways  $defaultgateway = $c.Defaultgateway[0]  Set-VBRDefaultGateway -Gateway $defaultgateway -IpAddress "172.16.2.232" -NetworkMask "255.255.0.0" |

Perform the following steps:

1. Run the [Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md) cmdlet. Save the result to the $config variable.
2. Get all default gateways by name. Save the array of gateways to the $alldefaultgateways variable.
3. Run the $alldefaultgateways variable to see all the names of all gateways available.
4. Select the first default gateway from the array. Save the result to the $config.Defaultgateway.name variable.
5. Run the Set-VBRDefaultGateway cmdlet. Set the $defaultgateway variable as the Gateway parameter value. Specify the IPAddress and the NetworkMask parameter values.

Related Commands

[Set-VBRDefaultGatewayConfiguration](set-vbrdefaultgatewayconfiguration.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
