---
title: "VEADContainer"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veadcontainer.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains information about a backed up Active Directory container.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Container ID. |
| Name | String | Container name. |
| DistinguishedName | String | Distinguished name (DN) of the container. |
| Parent | VEADContainer | Parent container. |
| Type | VEADContainerType | Container type. Possible values:   * UsersAndComputers * GroupPolicyObjects * IntegratedDNS * ConfigurationPartition * DfsConfiguration |

Related Commands

[Get-VEADContainer](get-veadcontainer.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
