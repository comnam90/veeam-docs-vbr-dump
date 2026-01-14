---
title: "vmrestorepoints_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmrestorepoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VM restore point having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmRestorePoints/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmRestorePoints/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/restorePoints/{ID}](restorepoints_id.md)
* [/backupFiles/{ID}](backupfiles_id.md)
* [/vmRestorePoints/{ID}/mounts](vmrestorepoints_id_mountpoint.md)

Methods

The following methods are supported for the /vmRestorePoints/{ID} resource:

* [GET /vmRestorePoints/{ID}](get_vmrestorepoints_id.md)
* [POST /vmRestorePoints/{ID}/mounts](post_vmrestorepoints_id_mountpoints.md)

Resource Representation

The /vmRestorePoints/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3" Name="oracle03@2016-10-06 13:59:50" UID="urn:veeam:VmRestorePoint:5acac742-ee17-4080-8e89-a6ea67adfcf3"> |

Entity resource representation:

|  |
| --- |
| <VmRestorePoint xmlns="http://www.veeam.com/ent/v1.0" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3?format=Entity" Name="oracle03@2016-10-06 13:59:50" UID="urn:veeam:VmRestorePoint:5acac742-ee17-4080-8e89-a6ea67adfcf3">   <Links>     <Link Rel="Restore" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3?action=restore" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />     <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/dc216c04-2e34-478e-8b9b-49a3397ef6f8" Name="Oct  6 2016  1:59PM" />     <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90" Name="Oracle BackupD2016-10-06T165918.vib" />     <Link Rel="Alternate" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3" Name="oracle03@2016-10-06 13:59:50" />     <Link Rel="Down" Type="VmRestorePointMountList" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3/mounts" />     <Link Rel="Create" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3/mounts" />   </Links>   <CreationTimeUTC>2016-10-06T13:59:50.783Z</CreationTimeUTC>   <Algorithm>Incremental</Algorithm>   <PointType>Increment</PointType>   <HierarchyObjRef>urn:HyperV:Vm:757baa80-d19b-4607-a592-98e15d45d9b2.e3e47ce3-ace6-4f06-9aaf-f52cf2e11234</HierarchyObjRef> </VmRestorePoint> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
