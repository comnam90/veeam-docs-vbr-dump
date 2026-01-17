---
title: "Cloud Connect Service"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloud_connect_service.html"
last_updated: "10/3/2025"
product_version: "13.0.1.1071"
---

# Cloud Connect Service


Service providers can use Veeam Backup Enterprise Manager REST API to manage Veeam Cloud Connect resources.

Veeam Cloud Connect resource URLs are grouped in the CloudConnectService resource. The resource contains links to the following resources:

* CloudGateway
* CloudTenant
* CloudHardwarePlan
* CloudPublicIpAddress
* CloudFailoverPlan
* CloudVmReplicaPoint
* CloudReplica
* VlanConfiguration
* CloudFailoverSession
* CloudGatewayPool
* CloudFailoveredVm

|  |
| --- |
| Note |
| * Veeam Cloud Connect is supported only on Windows-based installations of Enterprise Manager. * The CloudConnectService resource is available if the Veeam Cloud Connect service provider license is installed on the backup server. |

The resource representation of the Cloud Connect services is structured as follows:

|  |
| --- |
| <CloudConnectService Href="https://localhost:9398/api/cloud" Type="CloudConnectService" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |


