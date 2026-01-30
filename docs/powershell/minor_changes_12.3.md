---
title: "Minor Non-Breaking Change"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/minor_changes_12.3.html"
last_updated: "4/30/2025"
product_version: "13.0.1.1071"
---

# Minor Non-Breaking Change


The following minor non-breaking changes were introduced in Veeam PowerShell 12.

Backup

The Get-VBREncryptedBackup cmdlet was delivered as an alias for [Get-VBRImportedEncryptedBackup](get-vbrencryptedbackup.md). It allows to get a list of job IDs associated with encrypted backups.

Copy Job

In this version, in the following cmdlets parameters were changed from obligatory to non-required for the [Add-VBRCopyJob](add-vbrcopyjob.md) cmdlet:

* Folder
* Repository
* Server
* SourceServer


