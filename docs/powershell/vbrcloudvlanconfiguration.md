---
title: "VBRCloudVLANConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudvlanconfiguration.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# VBRCloudVLANConfiguration


Contains range of VLANs reserved for Veeam Backup & Replication.

Extended by:

* [VBRViCloudVLANConfiguration](#vi)
* [VBRHvCloudVLANConfiguration](#hv)

VBRViCloudVLANConfiguration

Properties

| Property | Type | Description |
| --- | --- | --- |
| Host | CHost | VMware host or cluster used as the replication target. |
| VirtualSwitch | VBRViServerNetworkInfo | VMware virtual switch connected to the target host. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform: VMware. |
| FirstVLANWithInternet | int32 | The first VLAN ID in the range of VLANs used for providing networks with internet access to VM replicas on the cloud host. |
| LastVLANWithInternet | int32 | The last VLAN ID in the range of VLANs used for providing networks with internet access to VM replicas on the cloud host. |
| FirstVLANWithoutInternet | int32 | The first VLAN ID in the range of VLANs used for providing networks without internet access to VM replicas on the cloud host. |
| LastVLANWithoutInternet | int32 | The last VLAN ID in the range of VLANs used for providing networks without internet access to VM replicas on the cloud host. |
| Id | GUID | VLAN ID. |

VBRHvCloudVLANConfiguration

Properties

| Property | Type | Description |
| --- | --- | --- |
| Host | Object | Hyper-V host or cluster used as the replication target. |
| VirtualSwitch | VBRHvServerNetworkInfo | Hyper-V virtual switch connected to the target host. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform: Hyper-V. |
| FirstVLANWithInternet | int32 | The first VLAN ID in the range of VLANs used for providing networks with internet access to VM replicas on the cloud host. |
| LastVLANWithInternet | int32 | The last VLAN ID in the range of VLANs used for providing networks with internet access to VM replicas on the cloud host. |
| FirstVLANWithoutInternet | int32 | The first VLAN ID in the range of VLANs used for providing networks without internet access to VM replicas on the cloud host. |
| LastVLANWithoutInternet | int32 | The last VLAN ID in the range of VLANs used for providing networks without internet access to VM replicas on the cloud host. |
| Id | GUID | VLAN ID. |


