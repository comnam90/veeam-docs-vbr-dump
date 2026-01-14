---
title: "Breaking Changes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/breaking_changes_v13.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Breaking Changes

In this article

This section contains information on breaking changes in Veeam PowerShell v13. These changes cause Veeam PowerShell v13 to function differently and could affect the code.

Renamed Cmdlets

In this version, the following cmdlets are renamed:

| Old Cmdlets | New Cmdlets |
| --- | --- |
| Apply-VBRIndependentRetention | [Apply-VBRBackgroundRetention](apply-vbrbackgroundretention.md) |
| Disable-VBRIndependentRetention | [Disable-VBRBackgroundRetention](disable-vbrbackgroundretention.md) |
| Enable-VBRIndependentRetention | [Enable-VBRBackgroundRetention](enable-vbrbackgroundretention.md) |

Deleted Cmdlets

Immutability

In this version, you can no longer roll back checkpoints in object storage repositories to the previous state. This functionality is no longer available in Veeam Backup & Replication. The following cmdlets are removed from the Veeam PowerShell module:

* Get-VBRObjectStorageRepositorySyncInterval
* Sync-VBRNASBackupState
* Sync-VBRObjectStorageRepositoryEntityState
* Sync-VBRUnstructuredBackupState

Storage Systems

In this version, the HPE StoreVirtual storage systems are no longer available in Veeam Backup & Replication. The following cmdlets are removed from the Veeam PowerShell module:

* Add-HP4Snapshot
* Add-HP4Storage
* Get-HP4Cluster
* Get-HP4InfrastructureVolume
* Get-HP4Snapshot
* Get-HP4Storage
* Get-HP4Volume
* Set-HP4Storage
* Sync-HP4Storage
* Sync-HP4Volume
* Remove-HP4Snapshot
* Remove-HP4Storage

Page updated 9/5/2025

Page content applies to build 13.0.1.1071
