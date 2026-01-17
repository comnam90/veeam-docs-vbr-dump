---
title: "/cloud/vmReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudvmreplicapoints.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/vmReplicaPoints


Represents a collection of restore points for separate VMs replicated with tenant replication jobs.

The collection includes restore points of the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/vmReplicaPoints |

Related Resources

[/cloud/vmReplicaPoints/{ID}](cloudvmreplicapoints_id.md)

Methods

The following methods are supported for the /cloud/vmReplicaPoints resource:

[GET /cloud/vmReplicaPoints](get_cloudvmreplicapoints.md)

Resource Representation

The /cloud/vmReplicaPoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


