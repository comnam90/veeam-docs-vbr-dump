---
title: "vesqlplugindatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlplugindatabase.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Microsoft SQL Server database backed up with Veeam Plug-in for Microsoft SQL Server.

| Property | Type | Description |
| --- | --- | --- |
| Name | String | Database name. |
| InstanceName | String | Instance name. |
| ServerName | String | DNS name or IP address of the source server. |
| ServerType | ServerType | Possible values:   * Unspecified * Standalone * Alwayson * Cluster |
| ProductVersion | System.Version | Microsoft SQL Server version of the instance on which the database is hosted. |

Related Commands

[Get-VESQLPluginDatabase](get-vesqlplugindatabase.md)

Page updated 11/10/2025

Page content applies to build 13.0.1.1071
