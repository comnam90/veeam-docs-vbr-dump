---
title: "Running Extract Utility in Interactive Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/extract_utility_console_interactive.html"
last_updated: "4/27/2026"
product_version: "13.0.1.2067"
---

# Running Extract Utility in Interactive Mode


This command runs the extract utility in the interactive mode.

Syntax

|  |
| --- |
| extract.exe [-password backupkey] [pathtobackup] |

Parameters

Parameters

| Parameter | Description | Required/Optional |
| password | Password for the encrypted backup file. | Required for encrypted backup files |
| pathtobackup | Path to the backup file from which machines must be restored. | Optional |

Example

This command validates an encrypted backup file.

|  |
| --- |
| extract.exe -password "standard 1" "C:/Backup/Single/Backup Job Single StorageD2022-10-03T132735\_1E50.vbk" |


