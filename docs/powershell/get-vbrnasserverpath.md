---
title: "Get-VBRNASServerPath"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasserverpath.html"
last_updated: "4/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNASServerPath

In this article

Short Description

Returns files paths to NFS network shared folders.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNASServerPath -Server <VBRUnstructuredServer>  [<CommonParameters>] |

Detailed Description

This cmdlet returns files paths to NFS network shared folders.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies NFS network shared folders. The cmdlet will return file paths to these shared folders. | Accepts the VBRUnstructuredServer object. To create this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASServerPath object that contains settings returns files paths to NFS network shared folders.

Examples

Getting Files Paths to NFS Network Shared Folders

This example shows how to get file path to the \\LinuxSRV2049\November share folder.

|  |
| --- |
| $server = Get-VBRUnstructuredServer -Name "\\LinuxSRV2049\November"  Get-VBRNASServerPath -Server $server |

Perform the following steps:

1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server parameter.
2. Run the Get-VBRNASServerPath cmdlet. Set the $server variable as the Server parameter value.

Related Commands

[Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)

Page updated 4/29/2024

Page content applies to build 13.0.1.1071
