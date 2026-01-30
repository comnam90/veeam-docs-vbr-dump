---
title: "VBRCloudTenantResource"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudtenantresource.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudTenantResource


Contains cloud user backup resources.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Repository | CBackupRepository | Backup repository whose space resources are allocated to the user. |
| RepositoryFriendlyName | string | Name of the cloud repository presented to the user. |
| RepositoryQuota | int | User account quota (MB). |
| RepositoryQuotaPath | string | Backup repository path. |
| UsedSpace | int | Space used by the tenant (MB). |
| PerformanceTierUsedSpace | int | Space used by capacity tier. |
| CapacityTierUsedSpace | int | Space used by performance tier. |
| ArchiveTierUsedSpace | int | Space used by archive tier. |
| UsedSpacePercentage | int | Space used by the tenant (percents). |
| WanAccelerationEnabled | bool | Indicates if the WAN accelerator is enabled (TRUE) or not (FALSE). |
| WanAccelerator | [CWanAccelerator](cwanaccelerator.md) | WAN accelerator used by the tenant. |

Related Commands

[Backup Resources](backup_resources.md)


