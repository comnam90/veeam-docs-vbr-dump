---
title: "VBRDiscoveredComputerUpdate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrdiscoveredcomputerupdate.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRDiscoveredComputerUpdate

In this article

Contains a Veeam Agent private fix.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | ulong | The issue number of the private fix. |
| Name | string | The name of the private fix. |
| AgentType | VBRAgentType | The type of a Veeam Agent:   * Windows * Linux |
| AgentVersion | Version | The version of the private fix. |
| OperatingSystemPlatform | VBROperatingSystemPlatform | The architecture of the Veeam Agent operating system:   * Unknown * x86 * x64 |
| OperatingSystemVersion | Version | The version of the Veeam Agent operating system. |
| Path | String | The full path to the folder on the distribution server where the private fix resides. |
| AppliedTo | Guid[] | The array of discovered computer IDs. The private fix is assigned to these discovered computers.  If this property is empty, the private fix is assigned to all discovered computers with Veeam Agents of a specified type. |

Related Commands

* [Get-VBRDiscoveredComputerUpdate](get-vbrdiscoveredcomputerupdate.md)
* [Set-VBRDiscoveredComputerUpdate](set-vbrdiscoveredcomputerupdate.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
