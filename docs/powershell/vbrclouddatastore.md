---
title: "VBRCloudDatastore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrclouddatastore.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudDatastore


Contains storage resources provided to tenant on service provider's cloud server.

Properties

| Property | Type | Description |
| --- | --- | --- |
| CloudServerId | GUID | Cloud server ID. |
| Capacity | int32 | Storage capacity (GB). |
| FreeSpace | int32 | Free space (GB). |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform. |
| Name | string | Storage name. |
| Id | GUID | Storage ID. |

Related Commands

[Get-VBRCloudDatastore](get-vbrclouddatastore.md)


