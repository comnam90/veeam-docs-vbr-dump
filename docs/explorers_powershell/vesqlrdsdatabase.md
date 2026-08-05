---
title: "VESQLRDSDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlrdsdatabase.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VESQLRDSDatabase


Contains details about a backed-up Microsoft SQL Server database running on Amazon RDS.

VESQLRDSDatabase

| Property | Type | Description |
| Name | String | Database name. |
| InstanceName | String | Instance name. |
| ServerName | String | DNS name or IP address of the source server. |
| ServerType | SQLRDSServerType | Possible values:   * Standalone * Alwayson * Cluster |
| ProductVersion | System.Version | Microsoft SQL Server version of the instance on which the database is hosted. |

Related Commands

[Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md)

Page updated 2026-01-27

