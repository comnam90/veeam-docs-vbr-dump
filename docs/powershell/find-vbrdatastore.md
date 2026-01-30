---
title: "Find-VBRDatastore (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrdatastore.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Find-VBRDatastore (obsolete)


Short Description

Returns a list of VMware datastores connected to the specified ESXi host.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to rewrite your scripts using the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. |

Applies to

Platform: VMware

Syntax

|  |
| --- |
| Find-VBRDatastore -Server <CHost> [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of all datastores connected to the specified ESXi host.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the ESXi host you want to get the list of the connected datastores of. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Name | Specifies the name of the datastore you want to get, or search conditions.  You can specify multiple names separated by commas. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Specific Datastore on Server

|  |  |
| --- | --- |
| This example shows how to look for the Store 04 datastore on server named VMwareHost.  |  | | --- | | Get-VBRServer -Name "VMwareHost" | Find-VBRDatastore -Name "Store 04" |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Find-VBRDatastore cmdlet. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Datastores on Server

|  |  |
| --- | --- |
| This example shows how to look for all datastores located on the VMwareHost server.  |  | | --- | | $server = Get-VBRServer -Name "VMwareHost"  Find-VBRDatastore -Server $server |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRDatastore cmdlet. Set the $server variable as the Server parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


