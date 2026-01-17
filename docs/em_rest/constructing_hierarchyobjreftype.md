---
title: "Constructing HierarchyObjRefType"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/constructing_hierarchyobjreftype.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Some requests in Veeam Backup Enterprise Manager REST API require the client to provide a reference to the virtual infrastructure object, or HierarchyObjRefType.

The HierarchyObjRefType object describes a specific node in the virtual infrastructure hierarchy. This object must be constructed for requests that refer to some node or level in the virtual infrastructure hierarchy, for example, a request editing a job or assigning a restore scope to the account in Veeam Backup Enterprise Manager.

The HierarchyObjRefType object is constructed as a string that has the following pattern:

|  |
| --- |
| urn:<Platform>:<Type>:<HierarchyRootId>.<ObjectRef> |

where:

* Platform is the platform on which the virtual infrastructure object is created: VMware, Hyperv or vCloud
* Type is the object type. In the VMware virtual environment, the HierarchyObjRefType can represent an object of the following types:

+ VM
+ Host
+ Cluster
+ Template
+ VirtualApp
+ Vc
+ Datacenter
+ Folder
+ Datastore
+ ComputeResource
+ ResourcePool
+ Tag
+ Category
+ StoragePod

In VMware Cloud Director, the HierarchyObjRefType can represent an object of the following types:

* VcdSystem
* Organization
* OrgVdc
* Vapp
* Vm
* VappTemplate
* VmTemplate

In the Hyper-V virtual environment, the HierarchyObjRefType can represent an object of the following types:

* Vm
* Host
* Cluster
* Scvmm
* HostGroup
* VmGroup

* HierarchyRootID is an ID of the host on which the virtual infrastructure object resides. The HierarchyRootID can be obtained using the [/hierarchyRoots](hierarchyroots.md) resource.
* ObjectRef is an ID of the virtual infrastructure object itself: mo-ref or ID, depending on the virtualization platform.

For example, you need to configure the HierarchyObjRefType string for the VM. The VM is described with the following settings:

* Platform: VMware
* Type: VM
* HierarchyRootID: vcprod.tech.local having ID a2b0c55d-829a-4efe-bd95-125ee77ba9dd
* Mo-ref: vm-7870

The HierarchyObjRefType string will then look in the following way:

|  |
| --- |
| urn:VMware:Vm:a2b0c55d-829a-4efe-bd95-125ee77ba9dd.vm-7870 |

|  |
| --- |
| Note |
| In addition to configuring the HierarchyObjRefType string manually, you can get the HierarchyObjRefType string for the necessary object in the virtual infrastructure hierarchy using the [/lookupSvc](lookupsvc.md) resource. |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
