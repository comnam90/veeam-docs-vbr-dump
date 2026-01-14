---
title: "publicipaddresses"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/publicipaddresses.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of all public IP addresses allocated in the service provider's network infrastructure added to pools of public IP addresses on backup servers connected to Veeam Backup Enterprise Manager. Public IP addresses can be assigned to tenants. Tenants can use public IP addresses to enable access to cloud VM replicas from the internet after full site failover.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses |

Related Resources

[/cloud/publicIpAddresses/{ID}](publicipaddresses_id.md)

Methods

The following methods are supported for the /cloud/publicIpAddresses resource:

* [GET /cloud/publicIpAddresses](get_publicipaddresses.md)
* [POST /cloud/publicIpAddresses](post_publicipaddresses.md)

Resource Representation

The /cloud/publicIpAddresses resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
