---
title: "Add-VBRNetAppNDMPServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrnetappndmpserver.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Add-VBRNetAppNDMPServer


Short Description

Adds NetApp NDMP servers.

Applies to

Product Edition: Enterprise

Syntax

|  |
| --- |
| Add-VBRNetAppNDMPServer -HostedServer <VBRNetAppNDMPHostedServer> -Credentials <CCredentials> -GatewayMode <VBRGatewayMode> [-SelectedGateway <CHost>] [<CommonParameters>] |

Detailed Description

This cmdlet adds a new NetApp NDMP server to the Veeam Backup & Replication infrastructure. Veeam Backup & Replication will use the specified credentials and settings to connect to the NDMP server.

The VBRNetAppNDMPHostedServer object is a NetApp NDMP-enabled Logical Interface (LIF). To create this object, add the NetApp host using the [Add-NetAppHost](add-netapphost.md) cmdlet with the EnableNDMPBackup parameter provided.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| HostedServer | Specifies the NetApp NDMP LIF that you want to add to Veeam Backup & Replication as an NDMP server. | Accepts the VBRNetAppNDMPHostedServer object. To get this object, run the [Get-VBRNetAppNDMPHostedServer](get-vbrnetappndmphostedserver.md) cmdlet. | True | Named | False |
| Credentials | Specifies the credentials. Veeam Backup & Replication will use these credentials to connect to the NetApp NDMP server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| GatewayMode | Specifies the gateway server selection mode. Veeam Backup & Replication will use this gateway server to connect to the NDMP server.  You can specify the following modes:   * Automatic — Veeam Backup & Replication automatically selects the gateway server. * SelectedGateway — specifies a particular gateway server explicitly. Use the SelectedGateway parameter to specify the server. | VBRGatewayMode | True | Named | False |
| SelectedGateway | For the SelectedGateway option in the GatewayMode parameter.  Specifies the server that you want to use as the gateway server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNetAppNDMPServer object that contains information about the NetApp NDMP server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding NetApp NDMP Server with Automatic Gateway Selection

|  |  |
| --- | --- |
| This example shows how to add a NetApp NDMP LIF as an NDMP server. Veeam Backup & Replication will select the gateway server automatically.  |  | | --- | | $netappHost = Get-NetAppHost -Name "172.18.12.1"  $hostedServer = Get-VBRNetAppNDMPHostedServer -Host $netappHost | Select-Object -First 1  $creds = Get-VBRCredentials -Name "ndmp-admin"  Add-VBRNetAppNDMPServer -HostedServer $hostedServer -Credentials $creds -GatewayMode Automatic |  Perform the following steps:   1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $netappHost variable. 2. Run the [Get-VBRNetAppNDMPHostedServer](get-vbrnetappndmphostedserver.md) cmdlet. Set the $netappHost variable as the Host parameter value. Save the result to the $hostedServer variable. 3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 4. Run the Add-VBRNetAppNDMPServer cmdlet. Specify the following settings:  * Set the $hostedServer variable as the HostedServer parameter value. * Set the $creds variable as the Credentials parameter value. * Set Automatic as the GatewayMode parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding NetApp NDMP Server with Manual Gateway Selection

|  |  |
| --- | --- |
| This example shows how to add a NetApp NDMP LIF as an NDMP server and choose a specific gateway server. Veeam Backup & Replication will use the specified server as the gateway server.  |  | | --- | | $netappHost = Get-NetAppHost -Name "172.18.12.1"  $hostedServer = Get-VBRNetAppNDMPHostedServer -Host $netappHost | Select-Object -First 1  $creds = Get-VBRCredentials -Name "ndmp-admin"  $gateway = Get-VBRServer -Name "172.18.1.50"  Add-VBRNetAppNDMPServer -HostedServer $hostedServer -Credentials $creds -GatewayMode SelectedGateway -SelectedGateway $gateway |  Perform the following steps:   1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $netappHost variable. 2. Run the [Get-VBRNetAppNDMPHostedServer](get-vbrnetappndmphostedserver.md) cmdlet. Set the $netappHost variable as the Host parameter value. Save the result to the $hostedServer variable. 3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 4. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $gateway variable. 5. Run the Add-VBRNetAppNDMPServer cmdlet. Specify the following settings:  * Set the $hostedServer variable as the HostedServer parameter value. * Set the $creds variable as the Credentials parameter value. * Set SelectedGateway as the GatewayMode parameter value. * Set the $gateway variable as the SelectedGateway parameter value. |

Related Commands

* [Get-NetAppHost](get-netapphost.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRNetAppNDMPHostedServer](get-vbrnetappndmphostedserver.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 2026-06-12

