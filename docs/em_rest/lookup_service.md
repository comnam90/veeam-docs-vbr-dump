---
title: "Virtual Infrastructure Lookup"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/lookup_service.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Virtual Infrastructure Lookup


The lookup service lets the client facilitate search for objects in the virtual infrastructure hierarchy: hosts, VMs, clusters, resource pools, folders and so on.

The lookup service is specifically targeted at retrieving resource representations of virtual infrastructure objects and references to virtual infrastructure objects. Object references are required for requests that refer to a specific node in the virtual infrastructure hierarchy. For example, to add a VM to the backup job, you need to provide a reference to this VM when sending a request for [job editing](put_jobs_id_actionedit.md). Similarly, to assign a restore scope to an account having a specific role in Veeam Backup Enterprise Manager, you need to provide a reference to the VM or VM container to which this account should have access.

The resource representation of the lookup service looks in the following way:

|  |
| --- |
| <LookupSvc xmlns="http://www.veeam.com/ent/v1.0" Type="LookupService" Href="https://localhost:9398/api/lookupSvc"> |

The lookup service resource representation contains a set of links to hierarchy roots — VMware and Hyper-V hosts added to backup servers that are managed by Veeam Backup Enterprise Manager. By following a link from the resource representation, the client can get a list of VMs that reside on a specific VMware or Hyper-V host. For VMware hosts, the client can also get a list of inventory object tags and storage pods (datastore clusters).

The resource representation of the lookup service provides links to hosts, VMs, tags and storage pods only and may be used for browsing. To obtain a reference to a specific virtual hierarchy object of other type, the client must construct a [query string to the lookup service](lookup_query.md) in a specific format.

|  |
| --- |
| Tip |
| The reference to the virtual infrastructure object can also be constructed manually. For details, see [Constructing HierarchyObjRefType](constructing_hierarchyobjreftype.md). |


