---
title: "Get-VBRDiscoveredComputer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdiscoveredcomputer.html"
last_updated: "10/13/2025"
product_version: "13.0.1.1071"
---

# Get-VBRDiscoveredComputer

In this article

Short Description

Returns discovered computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get discovered computers from all protection groups.

|  |
| --- |
| Get-VBRDiscoveredComputer [-Type <VBRDiscoveredEntityType[]> {Computer | Cluster | ActiveDirectory}]  [<CommonParameters>] |

* Get discovered computers from selected protection groups.

|  |
| --- |
| Get-VBRDiscoveredComputer [-ProtectionGroup <VBRProtectionGroup[]>] [-Type <VBRDiscoveredEntityType[]> {Computer | Cluster | ActiveDirectory}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns discovered computers from all protection groups or from selected protection groups. Use an appropriate parameter set for each case.

Veeam Backup & Replication regularly performs discovery operations for computers in a protection group. During a discovery operation, Veeam Backup & Replication connects to computers and gathers information about them. After the discovery operation is complete, Veeam Backup & Replication recognizes processed computers as discovered.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the array types:   * Computer: standalone computers * Cluster: computers that are part of a cluster  * ActiveDirectory: Active Directory computers   The cmdlet will return discovered computers of these types. | VBRDiscoveredEntityType[] | False | Named | True (ByProperty Name) |
| ProtectionGroup | Specifies the array of protection groups. The cmdlet will look for discovered computers in these groups. | Accepts the [VBRProtectionGroup](vbrprotectiongroup.md) object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDiscoveredComputer[]](vbrdiscoveredcomputer.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Discovered Computers of All Protection Groups

|  |  |
| --- | --- |
| This command returns discovered computers of all protection groups.  |  | | --- | | Get-VBRDiscoveredComputer | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Discovered Computers of Selected Protection Group

|  |  |
| --- | --- |
| This example shows how to get discovered computers of a selected protection group.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "Support\_East"  Get-VBRDiscoveredComputer -ProtectionGroup $group |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the Get-VBRDiscoveredComputer cmdlet. Set the $group variable as the ProtectionGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Active Directory Discovered Computers of Several Protection Groups

|  |  |
| --- | --- |
| This example shows how to get Active Directory discovered computers of several protection groups.  |  | | --- | | $groups = Get-VBRProtectionGroup -Name "Support\_East", "Support\_North"  Get-VBRDiscoveredComputer -Type ActiveDirectory -ProtectionGroup $groups |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $groups variable. 2. Run the Get-VBRDiscoveredComputer cmdlet. Set the ActiveDirectory option for the Type parameter. Set the $groups variable as the ProtectionGroup parameter value. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Rescan-VBREntity](rescan-vbrentity.md)

Page updated 10/13/2025

Page content applies to build 13.0.1.1071
