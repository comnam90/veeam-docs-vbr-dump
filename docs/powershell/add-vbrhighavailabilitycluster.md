---
title: "Add-VBRHighAvailabilityCluster"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhighavailabilitycluster.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Add-VBRHighAvailabilityCluster


Short Description

Assembles an HA cluster.

Applies to

Product Edition: Premium

Syntax

This cmdlet provides parameter sets that allow you to:

* Assemble an HA cluster within a single subnet.

|  |
| --- |
| Add-VBRHighAvailabilityCluster -PrimaryNodeIPAddress <String> -VBRHighAvailabilityClusterSecondaryNode <VBRHighAvailabilityClusterNode[]> -ClusterEndpoint <String> -ClusterDnsName <String> -Username <String> -Password <String> [-RunAsync] [-ForceAcceptCertificate]  [<CommonParameters>] |

* Assemble an HA cluster across multiple subnets.

|  |
| --- |
| Add-VBRHighAvailabilityCluster -PrimaryNodeIPAddress <String> -VBRHighAvailabilityClusterSecondaryNode <VBRHighAvailabilityClusterNode[]> -ClusterDnsName <String> -Username <String> -Password <String> [-RunAsync] [-ForceAcceptCertificate] -PrimaryNodeExternalEndpoint <String> -SecondaryNodeExternalEndpoint <String> [<CommonParameters>] |

Detailed Description

This cmdlet assembles an HA cluster.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| PrimaryNodeIPAddress | For assembling an HA cluster within a single subnet.  Specifies the IP address of the primary node.  Alias: PrimaryNodeHostName | String | True | Named | False |
| VBRHighAvailabilityClusterSecondaryNode | Specifies the secondary node. | Accepts the VBRHighAvailabilityClusterNode[] object. To create this object, run the [New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md) cmdlet. | True | Named | False |
| ClusterEndpoint | Specifies the static IP address of a cluster. | String | True | Named | False |
| ClusterDnsName | Specifies the DNS name of a cluster. | String | True | Named | False |
| PrimaryNodeExternalEndpoint | For assembling an HA cluster across multiple subnets.  Specifies the external IP address of the primary node. | String | True | Named | False |
| Username | Specifies the user name you want to use to authenticate with the secondary node. | String | True | Named | False |
| Password | Specifies the password you want to use to authenticate with the secondary node. | String | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| ForceAcceptCertificate | Defines that the cmdlet will accept the server certificate. | SwitchParameter | False | Named | False |
| SecondaryNodeExternalEndpoint | For assembling an HA cluster across multiple subnets.  Specifies the external IP address of the secondary node. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHighAvailabilityCluster](vbrhighavailabilitycluster.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Assembling an HA Cluster

|  |  |
| --- | --- |
| This example shows how to assemble the HA cluster.  |  | | --- | | $secondary = New-VBRHighAvailabilityClusterNode -HostName "203.0.113.24"  Add-VBRHighAvailabilityCluster -PrimaryNodeIPAddress 203.0.113.23 -VBRHighAvailabilityClusterSecondaryNode $secondary -ClusterEndpoint "203.0.113.25" -ClusterDnsName "ClusterSrv" -Username "veeamadmin" -Password \*\*\*\*\*\*\*\*\*\*\* -RunAsync -ForceAcceptCertificate |  Perform the following steps:   1. Run the [New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md) cmdlet. Specify the HostName parameter value. Save the result to the $secondary variable. 2. Run the Add-VBRHighAvailabilityCluster cmdlet. Specify the following settings:  * Specify the PrimaryNodeIPAddress parameter value. * Set the $secondary variable as the VBRHighAvailabilityClusterSecondaryNode parameter value. * Specify the ClusterDnsName parameter value. * Specify the Username parameter value. * Specify the Password parameter value. * Provide the RunAsync parameter. * Provide the ForceAcceptCertificate parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Assembling an HA Cluster Across Different Subnets

|  |  |
| --- | --- |
| This example shows how to assemble the HA cluster across different subnets.  |  | | --- | | $secondary = New-VBRHighAvailabilityClusterNode -HostName "203.0.113.34"  Add-VBRHighAvailabilityCluster -PrimaryNodeIPAddress 203.0.113.33 -VBRHighAvailabilityClusterSecondaryNode $secondary -ClusterDnsName "ClusterSrv" -Username "veeamadmin" -Password \*\*\*\*\*\*\*\*\*\*\* -PrimaryNodeExternalEndpoint "198.51.100.10" -SecondaryNodeExternalEndpoint "198.51.100.11" -RunAsync -ForceAcceptCertificate |  Perform the following steps:   1. Run the [New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md) cmdlet. Specify the HostName parameter value. Save the result to the $secondary variable. 2. Run the Add-VBRHighAvailabilityCluster cmdlet. Specify the following settings:  * Specify the PrimaryNodeIPAddress parameter value. * Set the $secondary variable as the VBRHighAvailabilityClusterSecondaryNode parameter value. * Specify the ClusterDnsName parameter value. * Specify the Username parameter value. * Specify the Password parameter value. * Specify the PrimaryNodeExternalEndpoint parameter value. * Specify the SecondaryNodeExternalEndpoint parameter value. * Provide the RunAsync parameter. * Provide the ForceAcceptCertificate parameter. |

Related Commands

[New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md)

Page updated 2026-06-29

