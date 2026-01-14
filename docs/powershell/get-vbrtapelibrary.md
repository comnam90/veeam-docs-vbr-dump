---
title: "Get-VBRTapeLibrary"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapelibrary.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTapeLibrary

In this article

Short Description

Returns tape libraries.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all tape libraries connected to a tape server.

|  |
| --- |
| Get-VBRTapeLibrary [-TapeServer <VBRTapeServer[]>]  [<CommonParameters>] |

* Get a tape library by ID.

|  |
| --- |
| Get-VBRTapeLibrary [-TapeServer <VBRTapeServer[]>] [-Id <guid[]>]  [<CommonParameters>] |

* Get a tape library by name.

|  |
| --- |
| Get-VBRTapeLibrary [-TapeServer <VBRTapeServer[]>] [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns tape libraries connected to Veeam Backup & Replication.

You can get the list of all tape libraries, narrow down your search to particular tape servers or search for instances directly by name or ID.

|  |
| --- |
| Note |
| Tape libraries are added to Veeam Backup & Replication automatically when you add a tape server with connected library. Run the [Add-VBRTapeServer](add-vbrtapeserver.md) cmdlet to add a tape server. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| TapeServer | Specifies the array of tape servers. The cmdlet will return tape libraries connected to these tape servers. | Accepts the [VBRTapeServer[]](vbrtapeserver.md) object, GUID or string type. To get this object, run the [Get-VBRTapeServer](get-vbrtapeserver.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the array of tape library names. The cmdlet will return tape libraries with these names. | String | False | Named | False |
| Id | Specifies the array of tape library IDs. The cmdlet will return tape libraries with these IDs. | Accepts GUID or string. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeLibrary[]](vbrtapelibrary.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Tape Libraries

|  |  |
| --- | --- |
| This command gets a list of all tape libraries connected to Veeam Backup & Replication.  |  | | --- | | Get-VBRTapeLibrary | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Tape Libraries Connected to Tape Server [Using Pipeline]

|  |  |
| --- | --- |
| This command looks for all tape libraries connected to the tape server named Sydney\_Tape\_Server.  |  | | --- | | Get-VBRTapeServer -Name "Sydney\_Tape\_Server" | Get-VBRTapeLibrary |  Perform the following steps:   1. Run the [Get-VBRTapeServer](get-vbrtapeserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRTapeLibrary cmdlet. |

Related Commands

[Get-VBRTapeServer](get-vbrtapeserver.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
