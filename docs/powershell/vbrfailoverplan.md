---
title: "VBRFailoverPlan"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrfailoverplan.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRFailoverPlan

In this article

Contains failover plan.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Failover plan ID. |
| Name | string | Failover plan name. |
| Description | string | Failover plan description. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform. |
| Status | string | Current status of the failover plan:   * In progress * Undo in progress * Completed * Ready * Failed * Undo failed |
| FailoverPlanObject | [VBRFailoverPlanObject](vbrfailoverplanobject.md)[] | VMs added to the failover plan. |
| VMCount | int | Number of VMs added to the failover plan. |
| PrefailoverCommand | string | Path to a script run automatically before failover. |
| PostfailoverCommand | string | Path to a script run automatically after failover. |
| Type | [VBRFailoverPlanType](enums.md#VBRFailoverPlanType) | Failover plan type: Local. |

Related Commands

[Failover Plans](fplan_cmdlets.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
