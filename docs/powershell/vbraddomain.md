---
title: "VBRADDomain"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbraddomain.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# VBRADDomain

In this article

Contains an Active Directory domain connection object.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | The connection object ID. |
| Name | string | The Active Directory domain name. |
| ServerName | string | The name for connecting to DC server/domain:   * DNS name for DC server * FQDN or NetBIOS for domain |
| Port | int | The port for authenticating with DC server/Domain. |
| Credentials | CCredentials | Credentials for authenticating with DC server/Domain. |

Related Commands

[Get-VBRADDomain](get-vbraddomain.md)

Page updated 5/20/2024

Page content applies to build 13.0.1.1071
