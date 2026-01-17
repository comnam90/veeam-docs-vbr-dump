---
title: "VEORRMANBackup"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veorrmanbackup.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about backups created with Veeam Plug-in for Oracle RMAN.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Backup ID. |
| Name | String | Backup name, in the following format:  <backup\_job>\<source\_machine\_dns\_name\_or\_ip\_address> Oracle backup (<backup\_repository>)  For example:  Oracle RMAN Plug-in Backup\WINORCL01 Oracle backup (Backup Repository 1) |
| ServerName | String | DNS name or IP address of the source server. |
| JobID | GUID | Backup job ID. |
| JobType | VEORRMANBackupJobType | Backup job type. Possible values:   * Backup * BackupCopy |

Related Commands

[Get-VEORRMANBackup](get-veorrmanbackup.md)

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
