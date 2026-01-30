---
title: "VBRTenantFailoverPlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtenantfailoverplan.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRTenantFailoverPlan


Contains tenant failover plan on service provider side.

Properties

| Property | Type | Description |
| --- | --- | --- |
| TenantId | GUID | ID of the tenant who created the failover plan. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform. |
| Status | string | The current status of the failover plan:   * In progress * Undo in progress * Completed * Ready * Failed * Undo failed |
| FailoverPlanObject | [VBRCloudFailoverPlanObject](vbrcloudfailoverplanobject.md)[] | Replica VM added to the cloud failover plan. |
| VMCount | int32 | Number of VMs added to the cloud failover plan. |
| PrefailoverCommand | string | Path to the script that must run before failover. |
| PostfailoverCommand | string | Path to the script that must run after failover. |
| Type | [VBRFailoverPlanType](enums.md#VBRFailoverPlanType) | Failover plan type: Tenant. |
| Id | GUID | Failover plan ID. |
| Name | string | Failover plan name. |
| Description | sting | Failover plan description. |


