---
title: "VEPSQLInstanceRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vepsqlinstancerestore.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEPSQLInstanceRestore


Contains details about a restored PostgreSQL instance.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Instance ID. |
| Session | GUID | Restore session ID. |
| RestorePointId | GUID | Restore point ID. |
| ToPointInTimeUTC | DateTime | Date and time in the UTC format of the state as of which the database is restored. |
| ServerName | String | DNS name or IP address of the target server for the restore operation. |
| InstanceName | String | Target instance name. |
| DataDirectory | String | Path to the data directory for the restored PostgreSQL instance. |
| RestoreStatus | String | Status of the restore operation. |

Related Commands

* [Start-VEPSQLInstanceRestore](start-vepsqlinstancerestore.md)
* [Get-VEPSQLInstanceRestore](get-vepsqlinstancerestore.md)
* [Restart-VEPSQLInstanceRestore](restart-vepsqlinstancerestore.md)
* [Stop-VEPSQLInstanceRestore](stop-vepsqlinstancerestore.md)


