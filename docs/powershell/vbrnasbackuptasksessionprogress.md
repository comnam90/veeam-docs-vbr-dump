---
title: "VBRNASBackupTaskSessionProgress"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnasbackuptasksessionprogress.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRNASBackupTaskSessionProgress

In this article

Contains file share backup task session progress.

Properties

| Property | Type | Description |
| --- | --- | --- |
| TaskSessionId | GUID | Task session ID. |
| IsTotalsSet | Bool | Indicates if the file share enumeration was finished. |
| TotalFiles | Int | Total number of files. |
| TotalFolders | Int | Total number of folders. |
| ReadFilesCount | Int | Total number of read files. |
| SkippedNotChangedFilesCount | Int | Total number of not changed and for that reason skipped files. |
| TransferredFilesCount | Int | Total number of transferred files. |
| ProcessedFilesCount | Int | Total number of processed files. |
| FoldersCount | Int | Total number of folders. |
| SkippedNotChangedSize | Int | Total size of not changed and for that reason skipped data. |
| ReportPath | String | Path to the backup task session report. |
| ExcludeFilesCount | Int | Total number of excluded files. |
| ExcludeFoldersCount | Int | Total number of excluded folders. |
| ProcessedSize | Int | Total size of processed data. |
| IsArchiveRun | Bool | Indicates if data was stored to the archive repository. |
| ArchivedFilesCount | Int | Total number of archived files. |
| ArchivedSize | Int | Total size of archived data. |
| SkippedLockedFilesCount | Int | Total number of locked and for that reason skipped files. |
| SkippedAccessDeniedFilesCount | Int | Total number of files with access denied and for that reason skipped. |
| SkippedAccessDeniedFoldersCount | Int | Total number of folders with access denied and for that reason skipped. |

Related Commands

[Get-VBRNASBackupTaskSession](get-vbrnasbackuptasksession.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
