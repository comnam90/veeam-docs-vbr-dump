---
title: "Find-VBRViStoragePolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrvistoragepolicy.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Find-VBRViStoragePolicy


Short Description

Looks for VMware storage policy profiles.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for all VMware storage policy profiles.

|  |
| --- |
| Find-VBRViStoragePolicy -Server <CHost> [-Datastore <CViDatastoreItem>]  [<CommonParameters>] |

* Look for a specific VMware storage policy profile by the storage policy profile name.

|  |
| --- |
| Find-VBRViStoragePolicy -Server <CHost> [-Datastore <CViDatastoreItem>] [-Name <string[]>]  [<CommonParameters>] |

* Look for a specific VMware storage policy profile by the storage policy profile ID.

|  |
| --- |
| Find-VBRViStoragePolicy -Server <CHost> [-Datastore <CViDatastoreItem>] [-Id <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns VMware storage policy profiles created on a vCenter Server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the vCenter Server where the storage policy profiles are created. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Datastore | Specifies a datastore. The cmdlet will return storage policy profiles compatible with this datastore. | Accepts the CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| Name | Specifies an array of storage policy profile names. The cmdlet will return profiles with these names. | String[] | False | Named | False |
| Id | Specifies an array of storage policy profile IDs. The cmdlet will return profiles with these IDs. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the [VBRViStoragePolicy](vbrvistoragepolicy.md)[] object that contains information on VMware storage policy profiles created on a vCenter Server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for all Storage Policy Profiles

|  |  |
| --- | --- |
| This example shows how to get a list of all storage policy profiles registered for the tech.local host.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "tech.local"  Find-VBRViStoragePolicy -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViStoragePolicy cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for Storage Policy Profile by its Name

|  |  |
| --- | --- |
| This example shows how to get the Virtual SAN Default Storage Policy storage policy profile registered for the tech.local host.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "tech.local"  Find-VBRViStoragePolicy -Server $server -Name "Virtual SAN Default Storage Policy" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViStoragePolicy cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Looking for Storage Policy Profile by its ID

|  |  |
| --- | --- |
| This example shows how to get the 4da512dc-dee7-465b-a507-72d44a9ba752 storage policy profile registered for the tech.local host.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "tech.local"  Find-VBRViStoragePolicy -Server $server -Id "4da512dc-dee7-465b-a507-72d44a9ba752" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViStoragePolicy cmdlet. Set the $server variable as the Server parameter value. Specify the Id parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)


