---
title: "restoresessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/restoresessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a restore session having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restoreSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restoreSessions/{ID}?format=Entity |

Related Resources

[/restoreSessions](restoresessions.md)

Methods

The following methods are supported for the /restoreSessions/{ID} resource:

[GET /restoreSessions/{ID}](get_restoresessions_id.md)

Resource Representation

The /restoreSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/676dc837-f441-4ac1-8470-15be06b4cffc" Name="FLR\_[srv04]@2014-10-19 05:59:18" UID="urn:veeam:RestoreSession:676dc837-f441-4ac1-8470-15be06b4cffc"> |

Entity resource representation:

|  |
| --- |
| <RestoreSession xmlns="http://www.veeam.com/ent/v1.0" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/676dc837-f441-4ac1-8470-15be06b4cffc?format=Entity" Name="FLR\_[srv04]@2014-10-19 05:59:18" UID="urn:veeam:RestoreSession:676dc837-f441-4ac1-8470-15be06b4cffc" VmDisplayName="srv04">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Alternate" Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/676dc837-f441-4ac1-8470-15be06b4cffc" Name="FLR\_[srv04]@2014-10-19 05:59:18" />     <Link Rel="Related" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85" Name="srv04@2014-10-19 05:25:15" />   </Links>   <JobType>FileLevelRestore</JobType>   <CreationTimeUTC>2014-10-19T05:59:18Z</CreationTimeUTC>   <EndTimeUTC>2014-10-19T06:28:24Z</EndTimeUTC>   <State>Stopped</State>   <Result>Success</Result>   <Progress>0</Progress> </RestoreSession> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
