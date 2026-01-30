---
title: "VBRCloudSubUser"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudsubuser.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudSubUser


Contains cloud subuser.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Cloud subuser ID. |
| Name | string | Cloud subuser name. |
| Password | string | Encrypted password hash. |
| Description | string | Cloud subuser description. |
| CloudProviderId | GUID | Parent cloud tenant ID. |
| Enabled | bool | Indicates if the cloud subuser is enabled (TRUE) or disabled (FALSE). |
| Resources | [VBRCloudSubUserResource](vbrcloudsubuserresource.md)[] | Quota of cloud subuser resources. |

Related Commands

[Cloud Subtenants](add-vbrcloudsubuser.md)

[Get-VBRCloudSubUser](get-vbrcloudsubuser.md)

[Set-VBRCloudSubUser](set-vbrcloudsubuser.md)

[Remove-VBRCloudSubUser](remove-vbrcloudsubuser.md)


