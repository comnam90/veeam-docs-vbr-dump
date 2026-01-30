---
title: "Get-VBRTapeServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapeserver.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTapeServer


Short Description

Returns tape servers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a list of tape servers created on specific hosts.

|  |
| --- |
| Get-VBRTapeServer [-Server <CHost[]>]  [<CommonParameters>] |

* Get a list of tape servers created on specific hosts by tape server name.

|  |
| --- |
| Get-VBRTapeServer [-Name <string[]>] [-Server <CHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns tape servers connected to the backup infrastructure.

You can get the list of all tape servers or narrow down the output to the servers of specific type, or search for instances directly by name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the array of hosts. The cmdlet will return tape servers created on these hosts. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the array of tape server names. The cmdlet will return tape servers with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeServer[]](vbrtapeserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of Tape Servers

|  |  |
| --- | --- |
| This command looks for all tape servers connected to Veeam Backup & Replication.  |  | | --- | | Get-VBRTapeServer | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting List of Tape Servers Connected to Host [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get all tape servers connected to the host named Host01.  |  | | --- | | Get-VBRServer -Name "Host01" | Get-VBRTapeServer |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRTapeServer cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Tape Server by Name [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get the tape server named Sydney\_Tape\_Server on the Host01 host.  |  | | --- | | $host01 = Get-VBRServer -Name "Host01"  Get-VBRTapeServer -Name "Sydney\_Tape\_Server" -Server $host01 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $host01 variable. 2. Run the Get-VBRTapeServer cmdlet. Specify the Name parameter value. Set the $host01 variable as the Server parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


