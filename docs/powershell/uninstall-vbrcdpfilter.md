---
title: "Uninstall-VBRCDPFilter"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrcdpfilter.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Uninstall-VBRCDPFilter

In this article

Short Description

Removes Veeam I/O filter from VMware clusters.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Uninstall-VBRCDPFilter -CDPCluster <CViClusterItem[]> [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Veeam I/O filters from VMware clusters.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CDPCluster | Specifies an array of VMware clusters from which you want to remove a Veeam I/O filter. | Accepts the  CViClusterItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| Force | Defines that the cmdlet will remove Veeam I/O filters from VMware clusters without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Veeam I/O filters from VMware Clusters

This example shows how to remove a Veeam I/O filter from the CDPCluster VMware cluster. The cmdlet will also remove the Veeam I/O filter from the CDPCluster.

|  |
| --- |
| $server = Get-VBRServer -Name "vCenterServer"  $cluster = Find-VBRViEntity -Server $server -HostsAndClusters -Name "CDPCluster"  Uninstall-VBRCDPFilter -CDPCluster $cluster |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Server, HostsAndClusters and Name parameters. Save the result to the $cluster variable.
3. Run the Uninstall-VBRCDPFilter cmdlet. Set the $cluster variable as the CDPCluster parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
