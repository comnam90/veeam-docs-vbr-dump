---
title: "VBRCloudGateway"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudgateway.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudGateway

In this article

Contains cloud gateway.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Host | CWinServer | Microsoft Windows server used as the cloud gateway. |
| Enabled | bool | Indicates if the gateway is enabled (TRUE) or disabled (FALSE). |
| NATPort | int | Port on the NAT gateway used for listening to connections from users and passing cloud commands from users to the SP Veeam backup server. |
| IncomingPort | int | Port used by the Veeam backup server to connect to the gateway. |
| IPAddress | string | External IP address of the NAT or network interface gateway. |
| NetworkMode | [VBRGatewayNetworkMode](enums.md#VBRGatewayNetworkMode) | Network mode. |
| Id | GUID | Unique cloud gateway ID. |
| Name | string | Cloud gateway name. |
| Description | string | Cloud gateway description. |

Related Commands

[Cloud Gateways](cloud_gateways.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
