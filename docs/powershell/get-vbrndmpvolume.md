---
title: "Get-VBRNDMPVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrndmpvolume.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNDMPVolume

In this article

Short Description

Returns NDMP server volumes.

Applies to

Product Edition: Enterprise

Syntax

This cmdlet provides parameter sets that allow you to:

* Get volumes by the volume name.

|  |
| --- |
| Get-VBRNDMPVolume [-Name <string[]>]  [<CommonParameters>] |

* Get volumes by the volume ID.

|  |
| --- |
| Get-VBRNDMPVolume -Id <guid[]>  [<CommonParameters>] |

* Get volumes on the specific NDMP server.

|  |
| --- |
| Get-VBRNDMPVolume -Server <VBRNDMPServer[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of NDMP server volumes.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of volume IDs. The cmdlet will return volumes with these IDs.  Note: You an array of volume IDs only after you create the file to tape job. | Guid[] | True | Named | False |
| Server | Specifies an array of NDMP servers. The cmdlet will return volumes located on these NDMP servers. | Accepts the [VBRNDMPServer](vbrndmpserver.md)[] object. To get this object, run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. | True | Named | False |
| Name | Specifies an array of names for volumes. The cmdlet will return volumes with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNDMPVolume](vbrndmpvolume.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Volumes of All NDMP Servers

|  |  |
| --- | --- |
| This command gets volumes of all NDMP servers added to Veeam Backup & Replication.  |  | | --- | | Get-VBRNDMPVolume | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting NDMP Server Volume by Volume ID

|  |  |
| --- | --- |
| This command gets an NDMP server volume by the volume ID.  |  | | --- | | Get-VBRNDMPVolume -ID "0fccf7c9-1f90-49de-8bec-53a0697e04ab" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting NDMP Server Volume by Volume ID

|  |  |
| --- | --- |
| This command gets an NDMP server volume by the volume name.  |  | | --- | | Get-VBRNDMPVolume -Name "/svm-cifs/Exhcange\_vol" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting All Volumes on Selected NDMP Server [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get all volumes on a specific NDMP server.  |  | | --- | | $server = Get-VBRNDMPServer -Name "NetApp.local"  Get-VBRNDMPVolume -Server $server |  Perform the following steps:   1. Run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Set-VBRNDMPServer cmdlet. Set the $server variable as Server parameter value. |

Related Commands

[Get-VBRNDMPServer](get-vbrndmpserver.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
