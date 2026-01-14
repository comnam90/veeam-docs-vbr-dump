---
title: "Breaking Changes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/breaking_changes_12.3.html"
last_updated: "11/25/2024"
product_version: "13.0.1.1071"
---

# Breaking Changes

In this article

This section contains information on breaking changes in Veeam PowerShell v12.3. These changes cause Veeam PowerShell v12.3 to function differently and could affect the client code.

Backup Infrastructure Components

Scale-Out backup Repositories

In this version, the following changes have been delivered for the [Add-VBRScaleOutBackupRepository](add-vbrscaleoutbackuprepository.md) and [Set-VBRScaleOutBackupRepository](set-vbrscaleoutbackuprepository.md) cmdlets:

* The EnableEncryption parameter is replaced with the EnableCapacityTierEncryption parameter.
* The EncryptionKey parameter replaced with CapacityTierEncryptionKey parameter.
* The KMSServer parameter replaced with CapacityTierKMSServer parameter.

Page updated 11/25/2024

Page content applies to build 13.0.1.1071
