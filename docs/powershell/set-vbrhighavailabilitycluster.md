---
title: "Set-VBRHighAvailabilityCluster"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhighavailabilitycluster.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRHighAvailabilityCluster


Short Description

Modifies settings of an HA cluster.

Applies to

Product Edition: Premium

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify settings of an HA cluster assembled within a single subnet.

|  |
| --- |
| Set-VBRHighAvailabilityCluster [-Cluster <VBRHighAvailabilityCluster>] [-ClusterEndpoint <String>] [-ClusterDnsName <String>]  [<CommonParameters>] |

* Modify settings of an HA cluster assembled across multiple subnets.

|  |
| --- |
| Set-VBRHighAvailabilityCluster [-Cluster <VBRHighAvailabilityCluster>] [-ClusterDnsName <String>] [-PrimaryNodeExternalEndpoint <String>] [-SecondaryNodeExternalEndpoint <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of an HA cluster. You can modify settings of an HA cluster assembled within a single subnet or of an HA cluster assembled across multiple subnets.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Cluster | Specifies the HA cluster you want to modify. | Accepts the VBRHighAvailabilityCluster object. To get this object, run the [Get-VBRHighAvailabilityCluster](get-vbrhighavailabilitycluster.md) cmdlet. | False | Named | True (ByValue) |
| ClusterDnsName | Specifies a DNS name of the cluster. | String | False | Named | False |
| ClusterEndpoint | Specifies an IP address that you want to assign to a high availability cluster. | String | False | Named | False |
| PrimaryNodeExternalEndpoint | For modifying an HA cluster assembled across multiple subnets.  Specifies the external IP address of the primary node. | String | False | Named | False |
| SecondaryNodeExternalEndpoint | For modifying an HA cluster assembled across multiple subnets.  Specifies the external IP address of the secondary node. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHighAvailabilityCluster](vbrhighavailabilitycluster.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Settings of HA Cluster Assembled in one Subnet

|  |  |
| --- | --- |
| This example shows how to modify settings of the HA cluster.  |  | | --- | | $cluster = Get-VBRHighAvailabilityCluster  Set-VBRHighAvailabilityCluster -Cluster $cluster -ClusterEndpoint 203.0.113.27 |  Perform the following steps:   1. Run the [Get-VBRHighAvailabilityCluster](get-vbrhighavailabilitycluster.md) cmdlet. Save the result to the $cluster variable. 2. Run the Set-VBRHighAvailabilityCluster cmdlet. Set the $cluster variable as the Cluster parameter value. Specify the ClusterEndpoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Settings of HA Cluster Assembled in Different Subnets

|  |  |
| --- | --- |
| This example shows how to modify the settings of the HA cluster assembled in different subnets.  |  | | --- | | $cluster = Get-VBRHighAvailabilityCluster  Set-VBRHighAvailabilityCluster -Cluster $cluster -PrimaryNodeExternalEndpoint "198.51.100.10" -SecondaryNodeExternalEndpoint "198.51.100.11" |  Perform the following steps:   1. Run the [Get-VBRHighAvailabilityCluster](get-vbrhighavailabilitycluster.md) cmdlet. Save the result to the $cluster variable. 2. Run the Set-VBRHighAvailabilityCluster cmdlet. Set the $cluster variable as the Cluster parameter value. Specify the following settings:  * Specify the PrimaryNodeExternalEndpoint parameter value. * Specify the SecondaryNodeExternalEndpoint parameter value. |

Related Commands

[Get-VBRHighAvailabilityCluster](get-vbrhighavailabilitycluster.md)

Page updated 2026-06-10

