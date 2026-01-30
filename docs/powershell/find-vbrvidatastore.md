---
title: "Find-VBRViDatastore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrvidatastore.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Find-VBRViDatastore


Short Description

Looks for VMware datastores.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for datastores connected to a specific host.

|  |
| --- |
| Find-VBRViDatastore -Server <CHost> [-Name <string[]>]  [<CommonParameters>] |

* Look for datastores compatible with a specific storage policy.

|  |
| --- |
| Find-VBRViDatastore -StoragePolicy <VBRViStoragePolicy> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet looks for VMware datastores connected to the specified ESXi host or that are compatible with a particular VMware storage policy profile.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an ESXi host. The cmdlet will return datastores connected to this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| StoragePolicy | Specifies the VMware storage policy profile. The cmdlet will return datastores compatible with this profile. | Accepts the [VBRViStoragePolicy](vbrvistoragepolicy.md) object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies an array of datastores names. The cmdlet will return datastores with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the CViDatastoreItem object that contains information on VMware datastores connected to the specified ESXi host or compatible with a specific storage policy.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for VMware Datastores Connected to Specific ESXi Host

|  |  |
| --- | --- |
| This example shows how to get a list of datastores connected to the esx05.tech.local ESXi hosts.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "esx05.tech.local"  Find-VBRViDatastore -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViDatastore cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for VMware Datastores Compatible with Specific Storage Policy Profiles

|  |  |
| --- | --- |
| This example shows how to get the list of the MSExchange datastores and datastores which names start with LocalStore\_0\*. These datastores are compatible with the SP Virtual SAN Default storage policy profile.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "esx05.tech.local"  $policy = Find-VBRViStoragePolicy -Server $server -Name "SP Virtual SAN Default"  Find-VBRViDatastore -StoragePolicy $policy -Name "MSExchange", "LocalStore\_0\*" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $policy variable. 3. Run the Find-VBRViDatastore cmdlet. Set the $policy variable as the StoragePolicy parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)


