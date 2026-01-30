---
title: "VBRCloudServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudserver.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudServer


Contains service provider cloud server.

Properties

| Property | Type | Description |
| --- | --- | --- |
| CloudProviderId | GUID | Service provider ID. |
| ApiVersion | string | Version of VMware vSphere API or Hyper-V server. |
| CPU | int32 | Quota of CPU resources assigned to the hardware plan (MHz). |
| Memory | int32 | Quota of memory resources assigned to the hardware plan (Mb). |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform. |
| Name | string | Server name. |
| Id | GUID | Server ID. |

Related Commands

[Get-VBRCloudServer](get-vbrcloudserver.md)


