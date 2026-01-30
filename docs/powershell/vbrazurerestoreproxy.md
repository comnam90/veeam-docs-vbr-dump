---
title: "VBRAzureRestoreProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazurerestoreproxy.html"
last_updated: "5/14/2025"
product_version: "13.0.1.1071"
---

# VBRAzureRestoreProxy


Contains Microsoft Azure proxy appliance.

Properties

| Property | Type | Description |
| --- | --- | --- |
| MaxConcurrentTasks | Int32 | Number of concurrent tasks. |
| TrafficPort | Int32 | Port number. |
| Subscription | [VBRAzureSubscription](vbrazuresubscription.md) | Microsoft Azure subscription. |
| Location | [VBRAzureLocation](vbrazurelocation.md) | Geographic location of Microsoft Azure datacenter. |
| VmSize | [VBRAzureVMSize](vbrazurevmsize.md) | Microsoft Azure VM configuration option. |
| StorageAccount | [VBRAzureStorageAccount](vbrazurestorageaccount.md) | Microsoft Azure storage account. |
| ResourceGroup | [VBRAzureResourceGroup](vbrazureresourcegroup.md) | Microsoft Azure resource group. |
| DnsNameLabel | String | Name of the dynamic public IP. |
| VirtualNetwork | [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) | Microsoft Azure virtual network. |
| VirtualSubnet | [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) | Microsoft Azure virtual network subnet. |

Related Commands

* [Add-VBRAzureRestoreProxy](add-vbrazurerestoreproxy.md)
* [Get-VBRAzureRestoreProxy](get-vbrazurerestoreproxy.md)


