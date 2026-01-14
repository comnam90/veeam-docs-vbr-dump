---
title: "VBRCloudServerNetworkInfo"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudservernetworkinfo.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudServerNetworkInfo

In this article

Contains networks connected to service provider cloud server.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform. |
| CloudServerId | GUID | Cloud server ID. |
| Type | [VBRViNetworkInfoType](enums.md#VBRViNetworkInfoType) | Network type: Cloud. |
| Name | string | Network name. |
| Id | GUID | Network ID. |

Related Commands

[Get-VBRCloudServerNetworkInfo](get-vbrcloudservernetworkinfo.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
