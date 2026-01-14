---
title: "VBRScaleOutBackupRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrscaleoutbackuprepository.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRScaleOutBackupRepository

In this article

Contains scale-out backup repository.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Unique identifier of the scale-out repository. |
| Name | string | The name of the scale-out repository. |
| Description | string | The description of the scale-out repository. |
| PolicyType | [VBRScaleOutBackupRepositoryPolicyType](enums.md#VBRScaleOutBackupRepositoryPolicyType) | Scale-out backup repository policy. |
| Extent | [VBRRepositoryExtent](vbrrepositoryextent.md) | The list of extents added to the scale-out repository. |
| UsePerVMBackupFiles | bool | Indicates if each VM in a job targeted to this repository will be stored as a separate chain of files (full backups and increments). |
| PerformFullWhenExtentOffline | bool | Indicates if the jobs targeted to this repository will create an active full backup if the extent with previous backup file is offline. |

Related Commands

[Scale-Out Backup Repositories](scale_out_repository.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
