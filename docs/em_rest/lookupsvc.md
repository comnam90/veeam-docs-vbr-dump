---
title: "/lookupSvc"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/lookupsvc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /lookupSvc


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
| <LookupSvc xmlns="http://www.veeam.com/ent/v1.0" Type="LookupService" Href="https://localhost:9398/api/lookupSvc">   <Links>     <Link Rel="Up" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/25df603f-1d53-4c3f-9c09-f94455ed7258" />     <Link Rel="Down" Type="HierarchyItemList" Href="https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:0d7ea80c-6ac8-46bf-863c-3a6093f8baec&name=\*&type=Vm" />     <Link Rel="Down" Type="HierarchyItemList" Href="https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:15410946-fc21-4b82-a53a-717478eae90f&name=\*&type=Vm" />     <Link Rel="Down" Type="HierarchyItemList" Href="https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:9f591b3b-0072-4326-9bcc-9dabb4218df5&name=\*&type=Vm" />     <Link Rel="Down" Type="HierarchyItemList" Href="https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:d63a6e79-e771-4c77-80be-ad7b6edc2ba7&name=\*&type=Vm" />     <Link Rel="Down" Type="HierarchyItemList" Href="https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:2dcfebc9-eb06-4d3b-a639-c1cfa8483621&name=\*&type=Vm" />     <Link Rel="Down" Type="HierarchyItemList" Href="https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:ca2f751f-8f26-4f39-815e-ce493b61fd80&name=\*&type=Vm" />     <Link Rel="Down" Type="HierarchyItemList" Href="https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:87f30351-3f9a-484a-8158-e51c35550d58&name=\*&type=Vm" />   </Links> </LookupSvc> |

Page updated 2026-07-29

