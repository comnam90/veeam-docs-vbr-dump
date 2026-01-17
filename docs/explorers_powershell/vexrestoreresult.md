---
title: "VEXRestoreResult"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vexrestoreresult.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Veeam Explorer for Microsoft Exchange item restore process.

| Property | Type | Description |
| --- | --- | --- |
| Name | DateTime | Name of the restored item. |
| Error | String | Error that occurred during the restore operation. |
| Warnings | String[] | Array of warnings that appeared during the restore operation. |
| CreatedCount | Ulong | Number of missing items that were restored from the backup. |
| MergedCount | Ulong | Number of changed items restored from the backup. |
| FailedCount | Ulong | Number of items for which the restore operation failed. |
| SkippedCount | Ulong | Number of items that were not changed or missing in the original location. Such items are skipped during the restore operation. |
| Results | [VEXItemRestoreResult](vexitemrestoreresult.md)[] | Details about the restore process of the child items. |

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
