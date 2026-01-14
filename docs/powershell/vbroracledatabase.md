---
title: "VBROracleDatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbroracledatabase.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# VBROracleDatabase

In this article

Contains job session.

Properties

| Property | Type | Description |
| --- | --- | --- |
| RestorePointID | GUID | The Oracle database restore point ID. |
| ServerName | string | The domain name of the Oracle database host. |
| IsReadOnly | bool | Indicates that the Oracle database is read-only (TRUE) or not (FALSE). |
| CreationTime | DateTime | The date and time of the Oracle database creation. |
| GuestOsType | [VBRGuestOsType](enums.md#VBRGuestOsType) | Oracle database guest OS type. |
| RecoveryModel | [VBROracleDatabaseRecoveryModel](enums.md#VBROracleDatabaseRecoveryModel) | Oracle database recovery mode. |
| Home | [VBROracleHomeInfo](#home) | The Oracle home. |
| Sid | string | The Oracle database ID. |
| GlobalName | string | The Oracle database global name. |
| FastRecoveryAreaPath | string |  |
| ControlFiles | [VBROracleDatabaseFileInfo](#file) | The Oracle database control file. |
| DataFiles | [VBROracleDatabaseFileInfo](#file) | The Oracle database data files. |
| LogFiles | [VBROracleDatabaseLogFileInfo](#log) | The Oracle database log files. |
| TempFiles | [VBROracleDatabaseFileInfo](#file) | The Oracle database temp files. |
| Name | string | The Oracle database name. |
| Id | GUID | The Oracle database ID in Veeam Backup & Replication. |

VBROracleDatabaseFileInfo

The Oracle database files.

| Property | Type | Description |
| --- | --- | --- |
| Path | string | The file path. |
| Size | UInt64 | The file size (bytes). |

VBROracleDatabaseLogFileInfo

The Oracle database log files.

| Property | Type | Description |
| --- | --- | --- |
| GroupNumber | string | The log files group number. |
| Path | string | The log file path. |
| Size | UInt64 | The log file size (bytes). |

VBROracleHomeInfo

The Oracle home information.

| Property | Type | Description |
| --- | --- | --- |
| Path | string | The Oracle home path. |
| Version | string | The Oracle product version. |
| IsAsm | bool | Indicates if the Oracle home uses ASM (TRUE) or not (FALSE). |
| Name | string | The Oracle home name. |

Related Commands

[Get-VBROracleDatabase](get-vbroracledatabase.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
