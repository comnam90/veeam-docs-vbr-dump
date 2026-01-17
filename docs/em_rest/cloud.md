---
title: "/cloud"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloud.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud


Represents a collection of Veeam Cloud Connect resources.

The /cloud resource provides a set of links to the following Veeam Cloud Connect resources:

* [CloudGateway](cloudgateways.md)
* [CloudGatewayPool](cloudgatewaypools.md)
* [CloudTenant](tenants.md)
* [CloudHardwarePlan](hardwareplans.md)
* [CloudPublicIpAddress](publicipaddresses.md)
* [CloudFailoverPlan](cloudfailoverplans.md)
* [CloudVmReplicaPoint](cloudvmreplicapoints.md)
* [CloudReplica](cloudreplicas.md)
* [VlanConfiguration](vlans.md)
* [CloudFailoverSession](cloudfailoversessions.md)

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud |

Related Resources

None.

Methods

The following methods are supported for the /cloud resource:

[GET /cloud](get_cloud.md)

Resource Representation

The /cloud resource has a resource representation of the following type:

|  |
| --- |
| <CloudConnectService Href="http://local.host:9399/api/cloud" Type="CloudConnectService" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |


