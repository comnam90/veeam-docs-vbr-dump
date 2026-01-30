---
title: "New-VBRHighAvailabilityClusterNode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhighavailabilityclusternode.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# New-VBRHighAvailabilityClusterNode


Short Description

Defines settings of the secondary node of an HA cluster.

Applies to

Product Edition: Premium

Syntax

|  |
| --- |
| New-VBRHighAvailabilityClusterNode -HostName <String>  [<CommonParameters>] |

Detailed Description

This cmdlet defines the VBRHighAvailabilityClusterNode object. This object contains settings of the host that will be used as the secondary node of an HA cluster.

To assemble a HA cluster, run the [Add-VBRHighAvailabilityCluster](add-vbrhighavailabilitycluster.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| HostName | Specifies the IP address of the secondary node. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHighAvailabilityClusterNode](vbrhighavailabilityclusternode.md)

Examples

Defining Settings of Secondary Node for HA cluster

This command defines the settings of the secondary node for the HA cluster. Save the result to the $secondary variable.

|  |
| --- |
| $secondary = New-VBRHighAvailabilityClusterNode -HostName "203.0.113.24" |


