---
title: "Install-VBRCDPFilter"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/install-vbrcdpfilter.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Install-VBRCDPFilter

In this article

Short Description

Installs Veeam I/O filters on VMware clusters.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Install-VBRCDPFilter -CDPCluster <CViClusterItem[]> [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet installs Veeam I/O filters on VMware clusters.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CDPCluster | Specifies an array of VMware clusters on which you want to install a Veeam I/O filter. | Accepts the  CViClusterItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | False |
| Force | Defines that the cmdlet will install a Veeam I/O filter on a VMware cluster without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPFilter[] object that contains Veeam I/O filters that are installed on VMware clusters.

Examples

Installing Veeam I/O filter to VMware Cluster

This example shows how to install a Veeam I/O filter on the CDPCluster VMware cluster. The cmdlet will install the same version of the Veeam I/O filter on the CDPCluster.

|  |
| --- |
| $server = Get-VBRServer -Name "vCenterServer"  $cluster = Find-VBRViEntity -Server $server -HostsAndClusters -Name "CDPCluster"  Install-VBRCDPFilter -CDPCluster $cluster |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Server, HostsAndClusters and Name parameters. Save the result to the $cluster variable.
3. Run the Install-VBRCDPFilter cmdlet. Set the $cluster variable as the CDPCluster parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViEntity](find-vbrvientity.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
