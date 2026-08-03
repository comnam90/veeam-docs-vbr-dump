---
title: "Get-VBRNetAppNDMPHostedServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnetappndmphostedserver.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRNetAppNDMPHostedServer


Short Description

Returns NetApp NDMP LIFs.

Applies to

Product Edition: Enterprise

Syntax

|  |
| --- |
| Get-VBRNetAppNDMPHostedServer -Host <CNaHost> [<CommonParameters>] |

Detailed Description

This cmdlet returns the NDMP-enabled LIFs configured on the specified NetApp storage system. You can use the returned objects as input for the [Add-VBRNetAppNDMPServer](add-vbrnetappndmpserver.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Host | Specifies the NetApp storage system. The cmdlet will return an array of the NDMP-enabled LIFs configured on this host. | Accepts the CNaHost object. To get this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns an array of the VBRNetAppNDMPHostedServer objects that contain information about the NetApp NDMP LIFs.

Examples

Getting NetApp NDMP-enabled LIFs

This example shows how to get the NDMP-enabled LIFs configured on a NetApp storage system.

|  |
| --- |
| $netappHost = Get-NetAppHost -Name "172.18.12.1"  Get-VBRNetAppNDMPHostedServer -Host $netappHost |

Perform the following steps:

1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $netappHost variable.
2. Run the Get-VBRNetAppNDMPHostedServer cmdlet. Set the $netappHost variable as the Host parameter value.

Related Commands

[Get-NetAppHost](get-netapphost.md)

Page updated 2026-06-12

