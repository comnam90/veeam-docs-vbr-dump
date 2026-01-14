---
title: "vlans"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vlans.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of all virtual switches on which VLAN ranges for Veeam Cloud Connect Replication are reserved. VLANs are used for providing networking capabilities to tenant VM replicas. Virtual switches are configured on virtualization hosts that are used as a replication target and connected to backup servers managed by Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/vlans |

Related Resources

[/cloud/vlans/{ID}](vlans_id.md)

Methods

The following methods are supported for the /cloud/vlans resource:

[GET /cloud/vlans](get_vlans.md)

Resource Representation

The /cloud/vlans resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
