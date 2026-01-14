---
title: "VBREntraIDTenantBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidtenantbackup.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDTenantBackup

In this article

Contains settings of a Microsoft Entra ID tenant backup.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | Guid | ID of the backup. |
| Name | String | Name of the backup. |
| JobId | Guid | ID of the tenant backup job. |
| RepositoryId | Guid | ID of the Microsoft Entra ID repository where the backup is stored. |
| TenantId | Guid | ID of the backed-up tenant. |
| CreationTime | DateTime | Date when the backup was created. |

Related Commands

[Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
