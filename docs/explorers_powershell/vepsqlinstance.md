---
title: "VEPSQLInstance"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vepsqlinstance.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEPSQLInstance


Contains details about a PostgreSQL instance.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Instance ID. |
| Uid | Ulong | Database unique identifier (UID). |
| Name | String | Instance name. |
| Version | String | PostgreSQL version of the instance. |
| ServerName | String | DNS name or IP address of the source server. |
| ArchiveMode | Bool | If True, the instance operates in the Archive mode. |
| StopBackupLsn | Long | Last log sequence number in the write-ahead log in the restore point. |
| BacupRecId | Long | Backup record ID. |
| WalSegmentSize | Ulong | Write-ahead log segment size in bytes. |
| LastCheckpointTimeUTC | DateTime | Date and time of the latest available state on the backup file. |
| HbaFilePath | String | Path to configuration file for host-based authentication. Default file: pg\_hba.conf |
| IdentFilePath | String | Path to configuration file for user name mapping. Default file: pg\_ident.conf |
| ConfigFilePath | String | Path to main server configuration file. Default file: postgresql.conf |
| DataDirectory | String | Path to the data directory for the instance on the source server. |
| TableSpaces | [VEPSQLTableSpace](vepsqltablespace.md)[] | Array of PostgreSQL tablespace paths. |

Related Commands

[Get-VEPSQLInstance](get-vepsqlinstance.md)


