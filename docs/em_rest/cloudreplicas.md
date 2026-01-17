---
title: "/cloud/replicas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudreplicas.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of replicas created by tenants whose accounts are created on all backup servers connected to Veeam Backup Enterprise Manager.

The collection includes the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/replicas |

Related Resources

[/cloud/replicas/{ID}](cloudreplicas_id.md)

Methods

The following methods are supported for the /cloud/replicas resource:

[GET /cloud/replicas](get_cloudreplicas.md)

Resource Representation

The /cloud/replicas resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
