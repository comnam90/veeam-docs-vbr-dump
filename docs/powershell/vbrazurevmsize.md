---
title: "VBRAzureVMSize"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazurevmsize.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRAzureVMSize


Contains Microsoft Azure VM configuration option.

Properties

| Property | Type | Description |
| --- | --- | --- |
| SubscriptionId | GUID | ID of subscription with which the configuration option is associated. |
| Cores | int32 | Available number of cores. |
| Memory | int32 | Maximum amount of memory (Mb). |
| MaxDisks | int32 | Maximum number of data disks. |
| Location | string | Datacenter location. |
| Name | string | Virtual network name. |

Related Commands

[Get-VBRAzureVMSize](get-vbrazurevmsize.md)


