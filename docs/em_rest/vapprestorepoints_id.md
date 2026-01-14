---
title: "vapprestorepoints_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vapprestorepoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a vApp restore point having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vAppRestorePoints/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vAppRestorePoints/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/restorePoints/{ID}](restorepoints_id.md)

Methods

The following methods are supported for the /vAppRestorePoints/{ID} resource:

* [GET /vAppRestorePoints/{ID}](get_vapprestorepoints_id.md)
* [POST /vAppRestorePoints/{ID}?action=restore](post_vapprestorepoints_id_actionrestore.md)

Resource Representation

The /vAppRestorePoints/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/8832a359-6af3-44de-9ae9-91feeee0d8c5" Name="vApp2@2014-10-19 06:07:11" UID="urn:veeam:VAppRestorePoint:8832a359-6af3-44de-9ae9-91feeee0d8c5"> |

Entity resource representation:

|  |
| --- |
| <VAppRestorePoint xmlns="http://www.veeam.com/ent/v1.0" Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/8832a359-6af3-44de-9ae9-91feeee0d8c5?format=Entity" Name="vApp2@2014-10-19 06:07:11" UID="urn:veeam:VAppRestorePoint:8832a359-6af3-44de-9ae9-91feeee0d8c5" VAppDisplayName="vApp2">   <Links>     <Link Rel="Restore" Href="https://localhost:9398/api/vAppRestorePoints/8832a359-6af3-44de-9ae9-91feeee0d8c5?action=restore" />     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/5456cc77-bea7-48bc-9834-55bafd23760b" Name="Oct 19 2014  6:06AM" />     <Link Rel="Alternate" Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/8832a359-6af3-44de-9ae9-91feeee0d8c5" Name="vApp2@2014-10-19 06:07:11" />   </Links>   <CreationTimeUTC>2014-10-19T06:07:11Z</CreationTimeUTC>   <Algorithm>Incremental</Algorithm>   <PointType>Increment</PointType>   <HierarchyObjRef>urn:vCloud:Vapp:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:vapp:78dc1989-d3f3-4b32-a3a8-ad3d3cbbd295</HierarchyObjRef> </VAppRestorePoint> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
