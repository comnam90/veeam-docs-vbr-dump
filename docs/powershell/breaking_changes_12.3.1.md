---
title: "Breaking Changes"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/breaking_changes_12.3.1.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Breaking Changes


This section contains information on breaking changes in Veeam PowerShell v12.3.1. These changes cause Veeam PowerShell v12.3.1 to function differently and could affect the code.

Backup

Managing Backups

In this version, the following cmdlets are renamed:

| Old Cmdlets | New Cmdlets |
| --- | --- |
| Get-VBRImportedEncryptedBackup | [Get-VBREncryptedBackup](get-vbrencryptedbackup.md) |
| Get-VBRImportedEncryptedBackupHint | [Get-VBREncryptedBackupHint](get-vbrencryptedbackuphint.md) |

Veeam Cloud Connect

In this version, the Tenants parameter is replaced with the Resource parameter for the [Switch-VBRCloudTenantsQuotaRepositoryToSOBR](switch-vbrcloudtenantsquotarepositorytosobr.md) cmdlet.


