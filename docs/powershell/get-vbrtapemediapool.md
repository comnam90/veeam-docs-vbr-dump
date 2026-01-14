---
title: "Get-VBRTapeMediaPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapemediapool.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTapeMediaPool

In this article

Short Description

Returns media pools.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get media pools that use a specific library.

|  |
| --- |
| Get-VBRTapeMediaPool [-Library <VBRTapeLibrary[]>]  [<CommonParameters>] |

* Get media pools by ID.

|  |
| --- |
| Get-VBRTapeLibrary [-Library <VBRTapeLibrary[]>] [-Id <guid[]>]  [<CommonParameters>] |

* Get media pools by name.

|  |
| --- |
| Get-VBRTapeLibrary [-Library <VBRTapeLibrary[]>] [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns media pools managed by Veeam Backup & Replication.

The cmdlet returns simple, GFS and service media pools. You can get the list of media pools that use a specific library, or search for instances directly by name or ID.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Library | Specifies the array of tape libraries. The cmdlet will return media pools that belong to these tape libraries. | Accepts the [VBRTapeLibrary](vbrtapelibrary.md) object, GUID or string. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Id | Specifies the array of media pool IDs. The cmdlet will return media pools with these IDs. | Accepts GUID or string. | False | Named | False |
| Name | Specifies the array of media pool names. The cmdlet will return media pools with these names. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMediaPoolBase[]](vbrtapemediapoolbase.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of All Media Pools

|  |  |
| --- | --- |
| This command looks for the list of all media pools in Veeam Backup & Replication.  |  | | --- | | Get-VBRTapeMediaPool | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Media Pools by Name

|  |  |
| --- | --- |
| This command looks for the media pools named File Backup Media Pool and AppData GFS Media Pool.  |  | | --- | | Get-VBRTapeMediaPool -Name "File Backup Media Pool", "AppData GFS Media Pool" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Media Pools in Library [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for all media pools in the HP MSL G3 Series 3.00 library.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Get-VBRTapeMediaPool |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRTapeMediaPool cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Media Pools in Library by Name [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the media pools named AD Full Backup and SharePoint Full Backups in the HP MSL G3 Series 3.00 library.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Get-VBRTapeMediaPool -Name "AD Full Backup", "SharePoint Full Backups" |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRTapeMediaPool cmdlet. Specify the Name parameter value. |

Related Commands

[Get-VBRTapeLibrary](get-vbrtapelibrary.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
