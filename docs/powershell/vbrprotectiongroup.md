---
title: "VBRProtectionGroup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrprotectiongroup.html"
last_updated: "4/8/2024"
product_version: "13.0.1.1071"
---

# VBRProtectionGroup

In this article

Contains a Veeam Agent protection group.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | string | The protection group ID. |
| Name | string | The protection group name. |
| Description | string | The protection group description. |
| Enabled | bool | Indicates if automatic discovery for this protection group is enabled. |
| Type | VBRProtectionGroupType | The protection group type:   * Custom * ManuallyAdded |
| Container | VBRProtectionGroupContainer | The type of a protection scope for which this protection group is created:   * ActiveDirectory * IndividualComputers * CloudMachines * CSV * ManuallyDeployed |
| ScheduleOptions | [VBRProtectionGroupScheduleOptions](vbrprotectiongroupscheduleoptions.md) | The protection group discovery schedule. |
| DeploymentOptions | [VBRProtectionGroupDeploymentOptions](vbrprotectiongroupdeploymentoptions.md) | The protection group deployment settings. |

Related Commands

[Get-VBRProtectionGroup](get-vbrprotectiongroup.md)

Page updated 4/8/2024

Page content applies to build 13.0.1.1071
