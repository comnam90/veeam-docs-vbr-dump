---
title: "VBRSQLDatabase"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrsqldatabase.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRSQLDatabase


Contains database in backup.

Properties

| Property | Type | Description |
| --- | --- | --- |
| RestorePoint | GUID | ID of restore point containing the database. |
| ServerName | string | Host name where the database is located. |
| InstanceName | string | SQL instance name where the database is created. |
| IsSystem | bool | Indicates that this is a system database. |
| IsReadonly | bool | Indicates that the database is read only. |
| CreationTime | DateTime | The date of creation of the database. |
| Name | string | Database name. |
| Id | GUID | Database ID. |

Related Commands

[Get-VBRSQLDatabase](get-vbrsqldatabase.md)


