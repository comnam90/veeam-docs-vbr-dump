---
title: "VBRViCloudHardwarePlan"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvicloudhardwareplan.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRViCloudHardwarePlan

In this article

Contains VMware hardware plan.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Hardware plan ID. |
| Name | string | Hardware plan name |
| Description | string | Hardware plan description |
| Datastore | [VBRViCloudHardwarePlanDatastore](vbrvicloudhardwareplandatastore.md)[] | Array of the datastores used for storing user data. |
| CPU | int | Quota of CPU resources assigned to the hardware plan (MHz). |
| Memory | int | Quota of memory resources assigned to the hardware plan (Mb). |
| NumberOfNetWithInternet | int | Number of networks with access to the Internet assigned to the hardware plan. |
| NumberOfNetWithoutInternet | int | Number of networks without access to the Internet assigned to the hardware plan. |
| SubscribedTenantId | GUID[] | IDs of tenants subscribed to the hardware plan. |
| Host | CHost, CViClusterItem | VMware host or cluster whose resources of are exposed to the user by the hardware plan. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform: VMware. |

Related Commands

* [Add-VBRViCloudHardwarePlan](add-vbrvicloudhardwareplan.md)
* [Set-VBRViCloudHardwarePlan](set-vbrvicloudhardwareplan.md)
* [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md)
* [Remove-VBRCloudHardwarePlan](remove-vbrcloudhardwareplan.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
