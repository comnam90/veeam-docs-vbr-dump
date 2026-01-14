---
title: "VBRCloudSubUserResource"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudsubuserresource.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudSubUserResource

In this article

Contains quota of cloud subuser resources.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | If the quota is assigned to a subuser: cloud subuser ID.  If the quota is not assigned to any subuser: NULL. |
| CloudRepositoryId | GUID | Parent cloud tenant ID. |
| RepositoryFriendlyName | string | Cloud subuser quota name. |
| RepositoryQuota | int | Cloud subuser quota (Mb).  If the quota is set to Unlimited, this property shows the quota of the parent cloud tenant. |
| UsedSpace | int | Space used by the subuser (Mb). |
| UsedSpacePercentage | int | Space used by the subuser (percents). |
| IsUnlimited | bool | Indicates if the cloud subuser quota is unlimited (TRUE) or not (FALSE). |

Related Commands

* [New-VBRCloudSubUserResource](new-vbrcloudsubuserresource.md)
* [Set-VBRCloudSubUserResource](set-vbrcloudsubuserresource.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
