---
title: "/restoreSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/restoresessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /restoreSessions


Represents a collection of restore sessions performed on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restoreSessions |

Related Resources

[/restoreSessions/{ID}](restoresessions_id.md)

Methods

The following methods are supported for the /restoreSessions resource:

[GET /restoreSessions](get_restoresessions.md)

Resource Representation

The /restoreSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/676dc837-f441-4ac1-8470-15be06b4cffc" Name="FLR\_[srv04]@2025-10-19 05:59:18" UID="urn:veeam:RestoreSession:676dc837-f441-4ac1-8470-15be06b4cffc">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/676dc837-f441-4ac1-8470-15be06b4cffc?format=Entity" Name="FLR\_[srv04]@2025-10-19 05:59:18" />     </Links>   </Ref>   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/9e289dec-4c1d-4a76-bae0-2191104cb59d" Name="FLR\_[srv04]@2025-10-19 05:57:10" UID="urn:veeam:RestoreSession:9e289dec-4c1d-4a76-bae0-2191104cb59d">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/9e289dec-4c1d-4a76-bae0-2191104cb59d?format=Entity" Name="FLR\_[srv04]@2025-10-19 05:57:10" />     </Links>   </Ref>   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/6114f06d-143a-45be-9b07-371704f71092" Name="FLR\_[srv04]@2025-10-18 15:16:59" UID="urn:veeam:RestoreSession:6114f06d-143a-45be-9b07-371704f71092">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/6114f06d-143a-45be-9b07-371704f71092?format=Entity" Name="FLR\_[srv04]@2025-10-18 15:16:59" />     </Links>   </Ref>   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/c8fdd529-d4af-48b2-8ea0-5d8b91359929" Name="FLR\_[srv04]@2025-10-19 06:00:25" UID="urn:veeam:RestoreSession:c8fdd529-d4af-48b2-8ea0-5d8b91359929">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/c8fdd529-d4af-48b2-8ea0-5d8b91359929?format=Entity" Name="FLR\_[srv04]@2025-10-19 06:00:25" />     </Links>   </Ref>   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/e8cd647d-9f67-4919-ac7f-5fc014444458" Name="FLR\_[srv04]@2025-10-19 07:19:53" UID="urn:veeam:RestoreSession:e8cd647d-9f67-4919-ac7f-5fc014444458">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/e8cd647d-9f67-4919-ac7f-5fc014444458?format=Entity" Name="FLR\_[srv04]@2025-10-19 07:19:53" />     </Links>   </Ref>  </EntityReferences> |

Page updated 2026-07-29

