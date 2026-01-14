---
title: "Add-VBRWANAccelerator"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrwanaccelerator.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Add-VBRWANAccelerator

In this article

Short Description

Creates a new WAN accelerator.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRWANAccelerator -Server <CHost> [-Description <String>] [-CachePath <String>] [-CacheSize <UInt32>] [-CacheSizeUnit <ESizeUnit>] [-EnableHighBandwidthMode] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new WAN accelerator.

WAN accelerator is an architecture component that optimizes file transfer via WAN by means of data deduplication. The role of a WAN accelerator can be assigned to a dedicated Windows-based machine (physical or virtual). For best performance you should set a WAN accelerator on both source and target sides.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the server where WAN accelerator will be created.  Note: You can create WAN accelerator on Microsoft Windows servers only. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies the description of the WAN accelerator. | String | False | Named | False |
| CachePath | Specifies the path to the folder where WAN accelerator will be created. | String | False | Named | False |
| CacheSize | Specifies the cache folder capacity value.  Permitted values: 1 to 65535. | UInt32 | False | Named | False |
| CacheSizeUnit | Specifies the measure unit for the cache folder capacity.  Permitted values: GB or TB. | ESizeUnit | False | Named | False |
| EnableHighBandwidthMode | Enables the High bandwidth mode option.  For more information on the option, see the [Choose Server](https://helpcenter.veeam.com/docs/vbr/userguide/wan_server.html?ver=13) step of the Adding WAN Accelerators wizard in the Veeam Backup & Replication User Guide. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will creates a new WAN accelerator without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[CwanAccelerator](cwanaccelerator.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating WAN Accelerator [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create a new WAN accelerator on the Veeam backup server.  |  | | --- | | Get-VBRLocalhost | Add-VBRWANAccelerator -Description "WAN Accelerator 01" -CachePath "c:\WAN" -CacheSize 100 -CacheSizeUnit GB |  Perform the following steps:   1. Run the [Get-VBRLocalhost](get-vbrlocalhost.md) cmdlet. 2. Pipe the cmdlet output to the Add-VBRWANAccelerator cmdlet. Specify the following settings:  * Specify the Description parameter value. * Specify the CachePath parameter value. * Specify the CacheSize and the CacheSizeUnit parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating WAN Accelerator [Using Variable]

|  |  |
| --- | --- |
| This command creates a new WAN accelerator using variables.  |  | | --- | | $server = Get-VBRServer -Name "server01.tech.global"  Add-VBRWANAccelerator -Server $server -Description "WAN Accelerator 02" -CachePath "c:\WAN" -CacheSize 150 -CacheSizeUnit GB |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRWANAccelerator cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Description parameter value. * Specify the CachePath parameter value. * Specify the CacheSize and the CacheSizeUnit parameter values. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
