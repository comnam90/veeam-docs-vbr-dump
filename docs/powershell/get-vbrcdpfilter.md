---
title: "Get-VBRCDPFilter"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcdpfilter.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCDPFilter

In this article

Short Description

Returns a list of Veeam I/O filters that are installed on VMware clusters.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRCDPFilter [-Cluster <CViClusterItem[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of Veeam I/O filters that are installed on VMware clusters.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Cluster | Specifies an array of VMware clusters. The cmdlet will return Veeam I/O filters that are installed on these VMware clusters. | Accepts the  CViClusterItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | True (ByValue, ByPropertyName |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPFilter[] object that contains Veeam I/O filters that are installed on VMware clusters.

Examples

Getting Veeam I/O filters Installed on VMware Clusters

This example shows how to get Veeam I/O filters that are installed on the CDPCluster VMware cluster.

|  |
| --- |
| $server = Get-VBRServer -Name "vCenterServer"  $cluster = Find-VBRViEntity -Server $server -HostsAndClusters -Name "CDPCluster"  Get-VBRCDPFilter -Cluster $cluster |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Server, HostsAndClusters and Name parameters. Save the result to the $cluster variable.
3. Run the Get-VBRCDPFilter cmdlet. Set the $cluster variable as the Cluster parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
