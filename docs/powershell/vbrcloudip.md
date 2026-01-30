---
title: "VBRCloudIP"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudip.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudIP


Contains public IP address from public IP addresses pool.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Public IP address ID. |
| IpAddress | string | Public IP address. |
| TenantId | GUID? | If the public IP address is assigned to a tenant: the ID of the tenant who uses the public IP address.  If the IP address is not assigned to any tenant: NULL. |

Related Commands

* [Add-VBRCloudPublicIP](add-vbrcloudpublicip.md)
* [Get-VBRCloudPublicIP](get-vbrcloudpublicip.md)
* [Remove-VBRCloudPublicIP](remove-vbrcloudpublicip.md)


