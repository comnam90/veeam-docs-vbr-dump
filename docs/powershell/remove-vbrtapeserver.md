---
title: "Remove-VBRTapeServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrtapeserver.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRTapeServer

In this article

Short Description

Removes a specified tape server from the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRTapeServer -TapeServer <VBRTapeServer[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a specified tape server from Veeam Backup & Replication.

When you remove a tape server, Veeam Backup & Replication unassigns the tape server role from the server, so it is no longer used as a tape server. The actual server remains connected to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| TapeServer | Specifies the array of tape servers. The cmdlet will remove these tape servers. | Accepts the [VBRTapeServer[]](vbrtapeserver.md) object. To get this object, run the [Get-VBRTapeServer](get-vbrtapeserver.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Tape Server [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove a tape server named Sydney\_Tape\_Server.  |  | | --- | | Get-VBRTapeServer -Name "Sydney\_Tape\_Server" | Remove-VBRTapeServer |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRTapeServer cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Tape Server [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove Sydney\_Tape\_Server and NewYork\_Tape\_Server tape servers.  |  | | --- | | $SydneyTapeServer = Get-VBRTapeServer -Name "Sydney\_Tape\_Server"  $NewYorkTapeServer = Get-VBRTapeServer -Name "NewYork\_Tape\_Server"  Remove-VBRTapeServer -TapeServer $SydneyTapeServer, $NewYorkTapeServer |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $SydneyTapeServer variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $NewYorkTapeServer variable. 3. Run the Remove-VBRTapeServer cmdlet. Set the $SydneyTapeServer and $NewYorkTapeServer variables as the Server parameter values. |

Related Commands

[Get-VBRTapeServer](get-vbrtapeserver.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
