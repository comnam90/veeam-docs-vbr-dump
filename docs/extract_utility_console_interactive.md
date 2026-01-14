---
title: "Running Extract Utility in Interactive Mode"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/extract_utility_console_interactive.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Running Extract Utility in Interactive Mode

In this article

This command runs the extract utility in the interactive mode.

Syntax

|  |
| --- |
| extract.exe [-password backupkey] [pathtobackup] |

Parameters

| Parameter | Description | Required/Optional |
| --- | --- | --- |
| password | Password for the encrypted backup file. | Required for encrypted backup files |
| pathtobackup | Path to the backup file from which machines must be restored. | Optional |

Example

This command validates an encrypted backup file.

|  |
| --- |
| extract.exe -password "standard 1" "C:/Backup/Single/Backup Job Single StorageD2022-10-03T132735\_1E50.vbk" |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
