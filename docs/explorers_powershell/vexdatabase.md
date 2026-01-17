---
title: "VEXDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vexdatabase.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Microsoft Exchange database or organization.

| Property | Type | Description |
| --- | --- | --- |
| Name | String | The property value depends on whether the backup was created by Veeam Backup & Replication or Veeam Backup for Microsoft 365.   * [For Veeam Backup & Replication backups] Database name and extension. For example, ABC Company.edb. * [For Veeam Backup for Microsoft 365 backups] Microsoft Exchange organization name in the following format:   <organization\_name> (<backup\_job\_name>) (<date\_and\_time\_when\_restore\_session\_was\_created>)  For example:  qwbs.onmicrosoft.com (Backup job) (2/25/2025 6:36:00 PM)  Note that the backup job name is only displayed if you have specified the job name when starting the restore session. |
| DatabaseFile | String | The property value depends on whether the backup was created by Veeam Backup & Replication or Veeam Backup for Microsoft 365.   * [For Veeam Backup & Replication backups] Path to the database .edb or .adb file on the source server. * [For Veeam Backup for Microsoft 365 backups] Database store. |
| LogsFolder | String | [For Veeam Backup & Replication backups] Path to the logs folder. |

Related Commands

[Get-VEXDatabase](get-vexdatabase.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
