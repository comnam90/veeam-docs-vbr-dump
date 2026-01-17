---
title: "Lookup Query"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/lookup_query.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

To obtain a resource representation of a specific virtual infrastructure object, you need to construct a query string to the lookup service. The query string can be constructed in two ways:

* [Using the object reference](lookup_query.md#ref) — to get a resource representation of an object that has the specified object reference.
* [Using query parameters](lookup_query.md#params) — to get a list of references to objects that match the specified criteria.

Query String with Object Reference

If you have a reference to the virtual infrastructure object and want to get its resource representation, you can construct a query string of the following type:

|  |
| --- |
| https://localhost:9398/api/lookup?hierarchyRef={hierarchyRef} |

where &hierarchyRef={hierarchyRef} identifies a hierarchy object reference. The hierarchy object reference is a string that is constructed by specific rules. This parameter explicitly refers to the necessary virtual infrastructure object and lets retrieve its resource representation. For details, see [Constructing HierarchyObjRefType](constructing_hierarchyobjreftype.md).

The example below returns a resource representation of the VM having the following object reference: urn:vCloud:Vm:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:vm:6b2da27f-e653-495b-b515-2b18bbb4d3ec.

|  |
| --- |
| Request:  GET https://localhost:9398/api/lookup?hierarchyRef=urn:vCloud:Vm:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:vm:6b2da27f-e653-495b-b515-2b18bbb4d3ec    Response:  200 OK    Response Body:  <HierarchyItems xmlns="http://www.veeam.com/ent/v1.0"> |

Query String with Parameters

If you want to get object references for one or several virtual infrastructure objects that match a specific criterion, you can construct a query string of the following type:

|  |
| --- |
| https://localhost:9398/api/lookup?host={hostUID}&name=(objectName)&type=(objectType) |

where:

* ?host={hostUID} identifies a VMware vSphere or Microsoft Hyper-V host to which the virtual infrastructure object belongs, for example: 3afa099d3b-7376-49b1-884c-bb6fa47c7b1e
* name identifies a name of the object in the virtual infrastructure hierarchy, for example: DC-VM
* type identifies the object type, for example: VM

The client can use the following object types in the query string:

For the VMware virtual environments:

* VM
* Host
* Cluster
* Template
* VirtualApp
* Vc
* Datacenter
* Folder
* Datastore
* ComputeResource
* ResourcePool
* Tag
* Category
* StoragePod

For VMware Cloud Director:

* VcdSystem
* Organization
* OrgVdc
* Vapp
* Vm
* VappTemplate
* VmTemplate

For the Hyper-V virtual environments:

* Vm
* Host
* Cluster
* Scvmm
* HostGroup
* VmGroup

The example below returns a VM named DC that resides on the host having the following ID: fa099d3b-7376-49b1-884c-bb6fa47c7b1e.

|  |
| --- |
| Request:  GET https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:fa099d3b-7376-49b1-884c-bb6fa47c7b1e&name=DC&type=Vm    Response:  200 OK    Response Body:  <HierarchyItems xmlns="http://www.veeam.com/ent/v1.0">   <HierarchyItem Type="HierarchyItem">     <ObjectRef>urn:vCloud:Vm:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:vm:340be4d6-8657-4d70-92d7-41ac6298f688</ObjectRef>     <ObjectType>Vm</ObjectType>     <ObjectName>DC</ObjectName>   </HierarchyItem> </HierarchyItems> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
