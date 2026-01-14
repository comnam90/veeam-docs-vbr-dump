---
title: "Install-VBRAvailableUpdates"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/install-vbravailableupdates.html"
last_updated: "9/8/2025"
product_version: "13.0.1.1071"
---

# Install-VBRAvailableUpdates

In this article

Short Description

Installs available software updates on Linux-based servers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Install software updates on all Linux-based servers.

|  |
| --- |
| Install-VBRAvailableUpdates -InstallAll  [<CommonParameters>] |

* Install software updates on a specific list of Linux-based servers.

|  |
| --- |
| Install-VBRAvailableUpdates -ServerId <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet installs available software updates on all Linux-based servers or a specific list of Linux-based servers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstallAll | Defines if updates are installed on all Linux-based servers. | SwitchParameter | True | Named | False |
| ServerId | Specifies the Linux-based servers you want to install updates on. | Guid | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Installing Updates on all Linux-Based Servers

|  |  |
| --- | --- |
| This command installs software updates on all Linux-based servers.  |  | | --- | | Install-VBRAvailableUpdates -InstallAll | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Installing Updates on Specific Linux-Based Servers

|  |  |
| --- | --- |
| This example shows how to install software updates on the Linux-based servers with specific ID.  |  | | --- | | $LinuxServers = Get-VBRServer -Type "Linux"  Install-VBRAvailableUpdates -ServerId $LinuxServers.Id |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set Linux as the Type parameter value. Save the result to the $LinuxServers variable. 2. Run the Install-VBRAvailableUpdates cmdlet. Provide the Id property for the $LinuxServers variable and set it as the ServerId parameter value. |

Related Commands

[Get-VBRAvailableUpdates](get-vbravailableupdates.md)

Page updated 9/8/2025

Page content applies to build 13.0.1.1071
