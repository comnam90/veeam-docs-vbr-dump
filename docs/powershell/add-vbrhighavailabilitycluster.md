---
title: "Add-VBRHighAvailabilityCluster"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhighavailabilitycluster.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Add-VBRHighAvailabilityCluster

In this article

Short Description

Assembles an HA cluster.

Applies to

Product Edition: Premium

Syntax

|  |
| --- |
| Add-VBRHighAvailabilityCluster -PrimaryNodeHostName <String> -VBRHighAvailabilityClusterSecondaryNode <VBRHighAvailabilityClusterNode[]> -ClusterEndpoint <String> -ClusterDnsName <String> -Username <String> -Password <String> [-RunAsync] [-ForceAcceptCertificate]  [<CommonParameters>] |

Detailed Description

This cmdlet assembles an HA cluster.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| PrimaryNodeHostName | Specifies IP address of the primary node. | String | True | Named | False |
| VBRHighAvailabilityClusterSecondaryNode | Specifies the secondary node. | Accepts the VBRHighAvailabilityClusterNode[] object. To create this object, run the [New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md) cmdlet. | True | Named | False |
| ClusterEndpoint | Specifies the static IP address of a cluster. | String | True | Named | False |
| ClusterDnsName | Specifies a DNS name of a cluster. | String | True | Named | False |
| Username | Specifies the user name you want to use to authenticate with the secondary node. | String | True | Named | False |
| Password | Specifies the password you want to use to authenticate with the secondary node. | String | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| ForceAcceptCertificate | Defines that the cmdlet will accept the server certificate. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHighAvailabilityCluster](vbrhighavailabilitycluster.md)

Examples

Assembling HA cluster

This example shows how assemble the HA cluster.

|  |
| --- |
| $secondary = New-VBRHighAvailabilityClusterNode -HostName "203.0.113.24"  Add-VBRHighAvailabilityCluster -PrimaryNodeHostName 203.0.113.23 -VBRHighAvailabilityClusterSecondaryNode $secondary -ClusterEndpoint "203.0.113.25" -ClusterDnsName "ClusterSrv" -Username "veeamadmin" -Password \*\*\*\*\*\*\*\*\*\*\* -RunAsync -ForceAcceptCertificate |

Perform the following steps:

1. Run the [New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md) cmdlet. Specify the HostName parameter value. Save the result to the $secondary variable.
2. Run the Add-VBRHighAvailabilityCluster cmdlet. Specify the following settings:

* Specify the PrimaryNodeHostName parameter value.
* Set the $secondary variable as the VBRHighAvailabilityClusterSecondaryNode parameter value.
* Specify the ClusterDnsName parameter value.
* Specify the Username parameter value.
* Specify the Password parameter value.
* Provide the RunAsync parameter.
* Provide the ForceAcceptCertificate parameter.

Related Commands

[New-VBRHighAvailabilityClusterNode](new-vbrhighavailabilityclusternode.md)

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
