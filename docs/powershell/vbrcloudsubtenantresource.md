---
title: "VBRCloudSubtenantResource"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudsubtenantresource.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudSubtenantResource


Contains quota of cloud subtenant resources.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | If the quota is assigned to a subtenant: cloud subtenant ID.  If the quota is not assigned to any subtenant: NULL. |
| ParentId | GUID | Parent cloud tenant ID. |
| RepositoryFriendlyName | string | Cloud subtenant quota name. |
| RepositoryQuota | int | Cloud subtenant quota (Mb).  If the quota is set to Unlimited, this property shows the quota of the parent cloud tenant. |
| RepositoryQuotaPath | string | Path to repository folder containing quota allocated to a subtenant. |
| UsedSpace | int | Space used by the subtenant (Mb). |
| UsedSpacePercentage | int | Space used by the subtenant (percents). |
| IsUnlimited | bool | Indicates if the cloud subtenant quota is unlimited (TRUE) or not (FALSE). |

Related Commands

[New-VBRCloudSubTenantResource](new-vbrcloudsubtenantresource.md)

[Set-VBRCloudSubTenantResource](set-vbrcloudsubtenantresource.md)


