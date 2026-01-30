---
title: "Veeam Cloud Connect Hardware Plans"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/hardware_plans.html"
last_updated: "9/4/2023"
product_version: "13.0.1.1071"
---

# Veeam Cloud Connect Hardware Plans


Hardware plans are quotas of hardware resources for cloud replication. Hardware plans include:

* Access to the host where the tenants can register their replicas.
* A quota of the host CPU and memory.
* A quota of cloud storage for storing replicas data.
* Networks to which the tenants can connect their replicas.

Hardware Plans

| VMware | Hyper-V | Operation |
| --- | --- | --- |
| [Add-VBRViCloudHardwarePlan](add-vbrvicloudhardwareplan.md) | [Add-VBRHvCloudHardwarePlan](add-vbrhvcloudhardwareplan.md) | Creates a hardware plan |
| [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) | | Returns hardware plans |
| [Set-VBRViCloudHardwarePlan](set-vbrvicloudhardwareplan.md) | [Set-VBRHvCloudHardwarePlan](set-vbrhvcloudhardwareplan.md) | Modifies a hardware plan |
| [Remove-VBRCloudHardwarePlan](remove-vbrcloudhardwareplan.md) | | Removes hardware plan |

Hardware Plans Datastores

| VMware | Hyper-V | Operation |
| --- | --- | --- |
| [New-VBRViCloudHWPlanDatastore](new-vbrvicloudhwplandatastore.md) | [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md) | Creates cloud storage for tenants replication resources |
| [Set-VBRViCloudHWPlanDatastore](set-vbrvicloudhwplandatastore.md) | [Set-VBRHvCloudHWPlanDatastore](set-vbrhvcloudhwplandatastore.md) | Modifies cloud storage for tenants replication resources |

VLANs

| VMware | Hyper-V | Operation |
| --- | --- | --- |
| [New-VBRCloudVLANConfiguration](new-vbrcloudvlanconfiguration.md) | | Reserves a pool of VLANs |
| [Get-VBRCloudVLANConfiguration](get-vbrcloudvlanconfiguration.md) | | Returns reserved VLANs |
| [Set-VBRCloudVLANConfiguration](set-vbrcloudvlanconfiguration.md) | | Modifies settings of a VLANs pool |
| [Remove-VBRCloudVLANConfiguration](remove-vbrcloudvlanconfiguration.md) | | Removes a VLANs pool |
| [Get-VBRViVirtualSwitch](get-vbrvivirtualswitch.md) | — | Returns virtual switches |


