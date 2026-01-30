---
title: "Set-VBRViVirtualLabIPMappingRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvivirtuallabipmappingrule.html"
last_updated: "5/2/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViVirtualLabIPMappingRule


Short Description

Modifies static IP address mapping rules.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViVirtualLabIPMappingRule -Rule <VBRViVirtualLabIPMappingRule> [-ProductionNetwork <VBRViNetworkInfo>] [-IsolatedIPAddress <ipaddress>] [-AccessIPAddress <ipaddress>] [-IsolatedIPv6Address <ipaddress>] [-AccessIPv6Address <ipaddress>] [-Note <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies static IP address mapping rules.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Rule | Specifies a static IP mapping rule that you want to modify. | Accepts the VBRViVirtualLabIPMappingRule object. To create this object, run the [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md) cmdlet. | True | Named | True (ByValue, |
| ProductionNetwork | Specifies a production network with original VMs. The cmdlet will set up static mapping of IP address from this network with IP addresses from the isolated network. | Accepts the VBRViNetworkInfo object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| IsolatedIPAddress | Specifies an IPv4 address of an isolated network. The cmdlet will map this IP address with an IP address of a production network. | IPAddress | False | Named | False |
| AccessIPAddress | Specifies an IPv4 address of a production network. The cmdlet will map this IP address with an IP address of an isolated network. | IPAddress | False | Named | False |
| IsolatedIPv6Address | Specifies an IPv6 address of an isolated network. The cmdlet will map this IP address with an IP address of a production network. | IPAddress | False | Named | False |
| AccessIPv6Address | Specifies an IPv6 address of a production network. The cmdlet will map this IP address with an IP address of an isolated network. | IPAddress | False | Named | False |
| Note | Specifies notes that you want to assign to the static mapping settings. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViVirtualLabNetworkMappingRule object that defines static IP address mapping rules.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying IPv4 Address of Isolated Network

|  |  |
| --- | --- |
| This example shows how to modify an IPv4 address of isolated network for a static IP address mapping rule. The 172.17.53.75 IP of the isolated network will be mapped with the 172.17.53.162 IP address of the production network.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  $mapping = New-VBRViVirtualLabIPMappingRule -ProductionNetwork $network[2] -IsolatedIPAddress 172.17.53.15 -AccessIPAddress 172.17.53.162  Set-VBRViVirtualLabIPMappingRule -Rule $mapping -IsolatedIPAddress 172.17.53.75 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md) cmdlet. Specify the ProductionNetwork, IsolatedIPAddress and AccessIPAddress parameter values. Save the result to the $mapping variable. 4. Run the Set-VBRViVirtualLabIPMappingRule cmdlet. Set the $mapping variable as the Rule parameter value. Specify the IsolatedIPAddress parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying IPv6 Address of Isolated Network

|  |  |
| --- | --- |
| This example shows how to modify an IPv6 address of isolated network for a static IP address mapping rule. The fdd1:ab80:bb80:cc80:dd80:ee80:ff80:1 IP of the isolated network will be mapped with the fdd1:aa80:bb80:ac80:dd80:ee80:ff80:1 IP address of the production network.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  $mapping = New-VBRViVirtualLabIPMappingRule -ProductionNetwork $network[2] -IsolatedIPv6Address fdd1:aa80:bb80:cc80:dd80:ee80:ff80:1 -AccessIPv6Address fdd1:aa80:bb80:ac80:dd80:ee80:ff80:1  Set-VBRViVirtualLabIPMappingRule -Rule $mapping -IsolatedIPv6Address fdd1:ab80:bb80:cc80:dd80:ee80:ff80:1 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md) cmdlet. Specify the ProductionNetwork, IsolatedIPv6Address and AccessIPv6Address parameter values. Save the result to the $mapping variable. 4. Run the Set-VBRViVirtualLabIPMappingRule cmdlet. Set the $mapping variable as the Rule parameter value. Specify the IsolatedIPv6Address parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying IPv4 Address of Production Network

|  |  |
| --- | --- |
| This example shows how to modify an IPv4 address of a production network for a static IP address mapping rule. The 172.17.53.15 IP of the isolated network will be mapped with the 172.17.53.170 IP address of the production network.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  $mapping = New-VBRViVirtualLabIPMappingRule -ProductionNetwork $network[2] -IsolatedIPAddress 172.17.53.15 -AccessIPAddress 172.17.53.162  Set-VBRViVirtualLabIPMappingRule -Rule $mapping -AccessIPAddress 172.17.53.170 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md) cmdlet. Specify the ProductionNetwork, IsolatedIPAddress and AccessIPAddress parameter values. Save the result to the $mapping variable. 4. Run the Set-VBRViVirtualLabIPMappingRule cmdlet. Set the $mapping variable as the Rule parameter value. Specify the AccessIPAddress parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)
* [New-VBRViVirtualLabIPMappingRule](new-vbrvivirtuallabipmappingrule.md)


