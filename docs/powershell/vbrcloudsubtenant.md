---
title: "VBRCloudSubTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudsubtenant.html"
last_updated: "1/23/2024"
product_version: "13.0.1.1071"
---

# VBRCloudSubTenant


Contains cloud subtenant.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Cloud subtenant ID. |
| Name | string | Cloud subtenant name. The name is unique for the parent cloud tenant. |
| Description | string | Cloud subtenant description. |
| TenantId | GUID | Parent cloud tenant ID. |
| Enabled | bool | Indicates if the cloud subtenant is enabled (TRUE) or disabled (FALSE). |
| Password | string | Encrypted password hash. |
| Resources | [VBRCloudSubtenantResource](vbrcloudsubtenantresource.md)[] | Quota of cloud subtenant resources. |
| Mode | VBRCloudSubTenantMode | Specifies cloud tenant mode: Common or AgentManagement. |

Related Commands

* [Cloud Subtenants](add-vbrcloudsubtenant.md)
* [Get-VBRCloudSubTenant](get-vbrcloudsubtenant.md)
* [Set-VBRCloudSubTenant](set-vbrcloudsubtenant.md)
* [Remove-VBRCloudSubTenant](remove-vbrcloudsubtenant.md)


