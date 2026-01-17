---
title: "/cloud/replicas/{ID}/vmReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudreplicas_id_vmreplicapoints.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/replicas/{ID}/vmReplicaPoints


Represents a collection of restore points for separate VMs in a cloud replica with the specified ID.

The collection includes restore points of the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/replicas/{ID}/vmReplicaPoints |

Related Resources

* [/cloud/replicas/{ID}](cloudreplicas_id.md)
* [/cloud/vmReplicaPoints](cloudvmreplicapoints.md)

Methods

The following methods are supported for the /cloud/replicas/{ID}/vmReplicaPoints resource:

[GET /cloud/replicas/{ID}/vmReplicaPoints](get_cloudreplicas_id_vmreplicapoints.md)

Resource Representation

The /cloud/replicas/{ID}/vmReplicaPoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


