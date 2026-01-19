---
title: "/vmReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmreplicapoints.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /vmReplicaPoints


Represents a collection of restore points for separate replicated VMs.

|  |
| --- |
| Note |
| The /vmReplicaPoints resource represents only restore points created by regular replication jobs. Restore points created with tenant replication jobs targeted at the cloud host appear in the /cloud/vmReplicaPoints resource representation. |

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmReplicaPoints |

Related Resources

[/vmReplicaPoints/{ID}](vmreplicapoints_id.md)

Methods

The following methods are supported for the /vmReplicaPoints resource:

[GET /vmReplicaPoints](get_vmreplicapoints.md)

Resource Representation

The /vmReplicaPoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


