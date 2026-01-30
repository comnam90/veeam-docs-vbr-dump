---
title: "VBRHvCloudHardwarePlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrhvcloudhardwareplan.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRHvCloudHardwarePlan


Contains Hyper-V hardware plan.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Hardware plan ID. |
| Name | string | Hardware plan name. |
| Description | string | Hardware plan description. |
| Datastore | [VBRHvCloudHardwarePlanDatastore](vbrhvcloudhardwareplandatastore.md)[] | Array of datastores used for storing user data. |
| CPU | int | Quota of CPU resources assigned to the hardware plan (MHz). |
| Memory | int | Quota of memory resources assigned to the hardware plan (Mb). |
| NumberOfNetWithInternet | int | Number of networks with access to the Internet assigned to the hardware plan. |
| NumberOfNetWithoutInternet | int | Number of networks without access to the Internet assigned to the hardware plan. |
| SubscribedTenantId | GUID[] | IDs of tenants subscribed to the hardware plan. |
| Host | CHost | Hyper-V host whose resources of are exposed to the user by the hardware plan. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform: Hyper-V. |

Related Commands

* [Add-VBRHvCloudHardwarePlan](add-vbrhvcloudhardwareplan.md)
* [Set-VBRHvCloudHardwarePlan](set-vbrhvcloudhardwareplan.md)
* [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md)
* [Remove-VBRCloudHardwarePlan](remove-vbrcloudhardwareplan.md)


