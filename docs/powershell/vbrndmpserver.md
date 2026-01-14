---
title: "VBRNDMPServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrndmpserver.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRNDMPServer

In this article

Contains NDMP server details.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Name | string | The NDMP server name. |
| Port | int | The port used to connect to an NDMP server. |
| Credentials | CCredentials | The credentials used to connect to an NDMP server. |
| GatewayMode | VBRGatewayMode | The gateway server mode used to connect to the NDMP server:   * Automatic * Selected gateway |
| SelectedGatewayId | GUID | The ID of selected gateway server. |

Related Commands

[Get-VBRNDMPServer](get-vbrndmpserver.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
