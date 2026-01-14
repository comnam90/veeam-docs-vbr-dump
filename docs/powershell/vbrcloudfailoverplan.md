---
title: "VBRCloudFailoverPlan"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudfailoverplan.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRCloudFailoverPlan

In this article

Contains cloud failover plan.

Properties

| Property | Type | Description |
| --- | --- | --- |
| PublicIpEnabled | bool | Indicates if the tenant is enabled to use public IP addresses (TRUE) or not (FALSE). |
| ProviderId | GUID | Service provider ID. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform. |
| Status | string | Current status of the failover plan:   * In progress * Undo in progress * Completed * Ready * Failed * Undo failed |
| FailoverPlanObject | [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md)[] | Replica VM added to the cloud failover plan. |
| VMCount | int32 | Number of VMs added to the cloud failover plan. |
| PrefailoverCommand | string | Path to the script that must run before failover. |
| PostfailoverCommand | string | Path to the script that must run after failover. |
| Type | [VBRFailoverPlanType](enums.md#VBRFailoverPlanType) | Failover plan type: Cloud. |
| Id | GUID | Failover plan ID. |
| Name | string | Failover plan name. |
| Description | sting | Failover plan description. |

Related Commands

* [Add-VBRFailoverPlan](add-vbrfailoverplan.md)
* [Get-VBRFailoverPlan](get-vbrfailoverplan.md)
* [Set-VBRFailoverPlan](set-vbrfailoverplan.md)
* [Remove-VBRFailoverPlan](remove-vbrfailoverplan.md)
* [Start-VBRFailoverPlan](start-vbrfailoverplan.md)
* [Undo-VBRFailoverPlan](undo-vbrfailoverplan.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
