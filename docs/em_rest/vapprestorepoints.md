---
title: "/vAppRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vapprestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /vAppRestorePoints


Represents a collection of vApp restore points created on backup servers that are managed by Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vAppRestorePoints |

Related Resources

[vAppRestorePoints/{ID}](vapprestorepoints_id.md)

Methods

The following methods are supported for the /vAppRestorePoints resource:

[GET /vAppRestorePoints](get_vapprestorepoints.md)

Resource Representation

The /vAppRestorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/f139af13-0d49-49c1-bf88-8b2d0db621e3" Name="vApp2@2025-10-19 05:43:56" UID="urn:veeam:VAppRestorePoint:f139af13-0d49-49c1-bf88-8b2d0db621e3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/f3f9fa75-6984-451b-a8ca-f5a318161951" Name="Oct 19 2025  5:43AM" />       <Link Rel="Alternate" Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/f139af13-0d49-49c1-bf88-8b2d0db621e3?format=Entity" Name="vApp2@2025-10-19 05:43:56" />     </Links>   </Ref>   <Ref Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/8832a359-6af3-44de-9ae9-91feeee0d8c5" Name="vApp2@2025-10-19 06:07:11" UID="urn:veeam:VAppRestorePoint:8832a359-6af3-44de-9ae9-91feeee0d8c5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/5456cc77-bea7-48bc-9834-55bafd23760b" Name="Oct 19 2025  6:06AM" />       <Link Rel="Alternate" Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/8832a359-6af3-44de-9ae9-91feeee0d8c5?format=Entity" Name="vApp2@2025-10-19 06:07:11" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

