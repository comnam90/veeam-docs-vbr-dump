---
title: "VEHANABackup"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vehanabackup.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about backups created with Veeam Plug-in for SAP HANA.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Backup ID. |
| Name | String | Backup name, in the following format:  <backup\_job>\<source\_machine\_dns\_name\_or\_ip\_address> SAP backint backup (<backup\_repository>)  For example:  SAP HANA backup 1\saphana01 SAP backint backup (Backup Repository 2) |
| ServerName | String | DNS name or IP address of the source server. |

Related Commands

[Get-VEHANABackup](get-vehanabackup.md)

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
