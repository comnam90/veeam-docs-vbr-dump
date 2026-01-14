---
title: "Find-VBRViDatastoreCluster"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrvidatastorecluster.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Find-VBRViDatastoreCluster

In this article

Short Description

Looks for VMware datastore clusters.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for VMware datastore clusters on a specific server.

|  |
| --- |
| Find-VBRViDatastoreCluster -Server <Object> [-Name <string[]>]  [<CommonParameters>] |

* Look for VMware datastore clusters compatible with a selected storage policy.

|  |
| --- |
| Find-VBRViDatastoreCluster -StoragePolicy <VBRViStoragePolicy> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of VMware datastore clusters.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of datastore cluster names. The cmdlet will return clusters with these names. | String[] | False | Named | False |
| Server | Specifies a host or cluster. The cmdlet will return the datastore clusters created on this host or cluster. | Accepts the Object object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| StoragePolicy | Specifies the VMware storage policy profile. The cmdlet will return datastores clusters compatible with this profile. | Accepts the [VBRViStoragePolicy](vbrvistoragepolicy.md) object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the [VBRViDatastoreCluster](vbrvidatastorecluster.md) object that contains a list of VMware datastore clusters.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for VMware Datastores Clusters Connected to Specific ESXi Host

|  |  |
| --- | --- |
| This example shows how to look for VMware datastore clusters on the esx05.tech.local host.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "esx05.tech.local"  Find-VBRViDatastoreCluster -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViDatastoreCluster cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for VMware Datastores Clusters Compatible with Specific Storage Policy Profiles

|  |  |
| --- | --- |
| This example shows how to get the list of the vol2 cluster datastores and cluster datastores which names start with cluster0\*. These datastores are compatible with the SP Virtual SAN Default storage policy profile.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "esx05.tech.local"  $policy = Find-VBRViStoragePolicy -Server $server -Name "SP Virtual SAN Default"  Find-VBRViDatastoreCluster -StoragePolicy $policy -Name "vol2", "cluster0\*" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $policy variable. 3. Run the Find-VBRViDatastoreCluster cmdlet. Set the $policy variable as the StoragePolicy parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)

Page updated 2/5/2024

Page content applies to build 13.0.1.1071
