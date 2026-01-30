---
title: "Add-VBRTapeServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrtapeserver.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Add-VBRTapeServer


Short Description

Adds a tape server to Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRTapeServer [-Description <string>] [-Server <CHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a tape server to the Veeam Backup & Replication managing console.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Description | Specifies the description of the tape server. | String | False | Named | False |
| Server | Specifies the server you want to use as a tape server.  If not set, Veeam backup server will be used. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Force | Defines that the cmdlet will add the tape server to the current backup server, although this tape server is already added to another backup server. The current backup server will take the ownership of this tape server. | SwitchParameter | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeServer](vbrtapeserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Tape Server [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to add the WindowsServer01 server as a tape server using a pipeline output. The description is Sydney Office tape server.  |  | | --- | | Get-VBRServer -Name WindowsServer01 | Add-VBRTapeServer -Description "Sydney Office tape server" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Add-VBRTapeServer cmdlet. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Tape Server [Using Variable]

|  |  |
| --- | --- |
| This example shows how to add the WindowsServer01 server as a tape server using a variable.  |  | | --- | | $tapeserver = Get-VBRServer -Name WindowsServer01  Add-VBRTapeServer -Server $tapeserver |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $tapeserver variable. 2. Run the Add-VBRTapeServer cmdlet. Set the $tapeserver variable as the Server parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


