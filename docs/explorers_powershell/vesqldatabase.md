---
title: "vesqldatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqldatabase.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Microsoft SQL Server database.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Database ID. |
| Name | String | Database name. |
| ServerName | String | DNS name or IP address of the source server. |
| InstanceName | String | Instance name. |
| IsSystem | Bool | If True, the database is a system database. |
| IsReadonly | Bool | If True, the database is a operating in the Read-only mode. |
| IsBackedUp | Bool | If True, the database has been backed up. |
| IsHeuristic | Bool | If True, the database has been backed up with application-aware processing disabled. |
| AvailabilityGroupName | String | Always On availability group to which the database belongs. The field is empty if the database is not a part of an Always On availability group. |
| RecoveryModel | SqlDatabaseRecoveryModel | Database recovery model configured in the backup job. Possible values:   * Simple * Full * Bulk-logged   For more information, see the [Required Job Settings](https://helpcenter.veeam.com/docs/vbr/userguide/vesql_bu_job_settings.html?ver=13#recovery-model) section of the Veeam Explorers User Guide. |

Related Commands

[Get-VESQLDatabase](get-vesqldatabase.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
