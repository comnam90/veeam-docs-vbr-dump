---
title: "/lookupSvc"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/lookupsvc.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents the lookup service. It contains a set of links of lookup queries that are composed for each hierarchy root — VMware and Hyper-V hosts added to backup servers that are managed by Veeam Backup Enterprise Manager. For detail, see [Virtual Infrastructure Lookup](lookup_service.md).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/lookupSvc |

Related Resources

None.

Methods

The following methods are supported for the /lookupSvc resource:

* [GET /lookupSvc](get_lookupsvc.md)
* [GET /lookup?host={hostUID}&hierarchyRef={hierarchyRef}&name={objName}&type={objType}](get_lookup.md)

Resource Representation

The /lookupSvc resource has a resource representation of the following type:

|  |
| --- |
| <LookupSvc xmlns="http://www.veeam.com/ent/v1.0" Type="LookupService" Href="https://localhost:9398/api/lookupSvc"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
