---
title: "Find-VBRViFolder"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrvifolder.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# Find-VBRViFolder

In this article

Short Description

Looks for folders on a specified ESXi host.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Find-VBRViFolder -Server <CHost> [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns folders on a specified ESXi host.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an ESXi host on which you want to look for folders. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies an array of folder names. The cmdlet will return folders with these names. | String[] | False | Named | False |

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CViFolderItem object that cotains folders on a specified ESXi host.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for all Folders Located on ESXi Host

|  |  |
| --- | --- |
| This example shows how to look for all folders located on the Server01 ESXi host.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "Server01"  Find-VBRViFolder -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViFolder cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for Specific Folder Located on ESXi Host

|  |  |
| --- | --- |
| This example shows how to look for the Weekly\_Reports folder located on the Server01 ESXi host.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "Server01"  Find-VBRViFolder -Server $server -Name "Weekly\_Reports" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViFolder cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Looking for Several Specific Folders Located on ESXi Host

|  |  |
| --- | --- |
| This example shows how to look for the Weekly\_Reports and Monthly\_Report folders located on the Server01 ESXi host.  |  | | --- | | $server01 = Get-VBRServer -Name "Server01"  Find-VBRViFolder -Server $server01 -Name "Weekly\_Reports", "Monthly\_Reports" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server01 variable. 2. Run the Find-VBRViFolder cmdlet. Set the $server01 variable as the Server parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 5/20/2024

Page content applies to build 13.0.1.1071
