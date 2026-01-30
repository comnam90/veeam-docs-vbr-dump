---
title: "Get-VBRProtectionGroup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrprotectiongroup.html"
last_updated: "8/16/2024"
product_version: "13.0.1.1071"
---

# Get-VBRProtectionGroup


Short Description

Returns protection groups.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all protection groups.

|  |
| --- |
| Get-VBRProtectionGroup  [<CommonParameters>] |

* Get protection groups by ID.

|  |
| --- |
| Get-VBRProtectionGroup [-Id <guid[]>]  [<CommonParameters>] |

* Get protection groups by name.

|  |
| --- |
| Get-VBRProtectionGroup [-Name <string[]>]  [<CommonParameters>]>] |

* Get protection groups by type (Custom/ManuallyAdded).

|  |
| --- |
| Get-VBRProtectionGroup [-Type <VBRProtectionGroupType[]> {Custom | ManuallyAdded}]  [<CommonParameters>] |

* Get protection groups by protection scope (IndividualComputers/ActiveDirectory/CSV/ManuallyDeployed/CloudeMachines/MongoDBComputers).

|  |
| --- |
| Get-VBRProtectionGroup [-ContainerType <VBRProtectionGroupContainerType[]> {IndividualComputers | ActiveDirectory | CSV ManuallyDeployed | CloudMachines | MongoDBComputers}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns protection groups.

You can get all protection groups or search for instances directly by name, ID, type or protection scope. Use an appropriate parameter set for each case.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the array of protection group IDs. The cmdlet will return protection groups with these IDs. | Guid[] | False | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the array of protection group names. The cmdlet will return protection groups with these names. | String[] | False | Named | True (ByProperty Name) |
| Type | Specifies protection group types:   * Custom: protection groups created for individual computers, Active Directory objects, cloud machines, computers listed in a CSV file or MongoDB Replica sets. * ManuallyAdded: protection groups created for computers that were added manually to a Veeam Agent backup job.   The cmdlet will return protection groups of these types. | VBRProtectionGroupType[] | False | Named | True (ByProperty Name) |
| ContainerType | Specifies the array of protection scope types:   * ActiveDirectory: a scope of Active Directory objects. * IndividualComputers: a scope of individual computers. * CloudMachines: a scope of cloud machines. * CSV: a scope of computers listed in a CSV file. * ManuallyDeployed: a scope of computers with pre-installed Veeam Agents. * MongoDBComputers: a scope of MongoDB Replica sets.   The cmdlet will return protection groups created for these protection scope types. | VBRProtectionGroupContainerType[] | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRProtectionGroup[]](vbrprotectiongroup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Protection Groups

|  |  |
| --- | --- |
| This command returns all protection groups added to Veeam Backup & Replication.  |  | | --- | | Get-VBRProtectionGroup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Protection Groups by ID

|  |  |
| --- | --- |
| This command returns protection groups by ID.  |  | | --- | | Get-VBRProtectionGroup -Id 4022509c-3308-4883-b166-118bdf7480ea, 730dc485-84c2-4a9d-86e7-2e35d1d5a0be | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Protection Groups by Scope of Active Directory Objects

|  |  |
| --- | --- |
| This command returns protection groups created for the scope of Active Directory objects.  |  | | --- | | Get-VBRProtectionGroup -ContainerType ActiveDirectory | |


