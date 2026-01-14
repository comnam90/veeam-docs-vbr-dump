---
title: "VBRAzureLinuxRestoreAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazurelinuxrestoreappliance.html"
last_updated: "2/20/2024"
product_version: "13.0.1.1071"
---

# VBRAzureLinuxRestoreAppliance

In this article

Contains configuration of appliance for Linux VMs restore.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Type | [VBRAzureModelType](enums.md#VBRAzureModelType) | Microsoft Azure subscription type. |
| Subscription | [VBRAzureSubscription](vbrazuresubscription.md) | ID of subscription with which the configuration option is associated. |
| Location | [VBRAzureLocation](vbrazurelocation.md) | Geographic location of Microsoft Azure datacenter. |
| StorageAccount | [VBRAzureStorageAccount](vbrazurestorageaccount.md) | Microsoft Azure storage account. |
| VirtualNetwork | [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) | Microsoft Azure virtual network. |
| VirtualNetworkSubnet | [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) | Microsoft Azure virtual network subnet. |
| Id | GUID | Appliance ID. |

Related Commands

[New-VBRAzureLinuxRestoreAppliance](new-vbrazurelinuxrestoreappliance.md)

Page updated 2/20/2024

Page content applies to build 13.0.1.1071
