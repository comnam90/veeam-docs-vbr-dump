---
title: "/systemSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/systemsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /systemSessions


Represents a list of all system sessions of Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/systemSessions |

Related Resources

[/systemSessions/{ID}](systemsessions_id.md)

Methods

The following methods are supported for the /backupSessions resource:

[GET /systemSessions](get_systemsessions.md)

Resource Representation

The /systemSessions resource has a resource representation of the following type:

|  |
| --- |
| <SystemSessions xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Sessions Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25?format=Entity" Type="SystemSession" Name="Collect Job @2025-01-27 17:05:52.069837" UID="urn:veeam:SystemSession:00057ade-8f1a-4b54-a265-391441981e25">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25" Name="Collect Job @2025-01-27 17:05:52.069837" Type="BackupJobSessionReference" Rel="Alternate"/>       <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25/events" Name="Events" Type="SystemSessionEvents" Rel="Down"/>     </Links>     <SessionType>CollectJob</SessionType>     <CreationTimeUTC>2025-01-27T17:05:52.069837Z</CreationTimeUTC>     <EndTimeUTC>2025-01-27T17:06:10.491337Z</EndTimeUTC>     <State>CompletedSuccessfully</State>     <Result>       <Result>CompletedSuccessfully</Result>       <Message/>       <IsCanceled>false</IsCanceled>     </Result>   </Sessions>   <Sessions Href="https://enterprise04.tech.local:9398/api/systemSessions/00463c10-8196-4389-bd6b-8681c662e499?format=Entity" Type="SystemSession" Name="Catalog Replication Job @2025-01-30 16:38:54.377016" UID="urn:veeam:SystemSession:00463c10-8196-4389-bd6b-8681c662e499">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00463c10-8196-4389-bd6b-8681c662e499" Name="Catalog Replication Job @2025-01-30 16:38:54.377016" Type="BackupJobSessionReference" Rel="Alternate"/>       <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00463c10-8196-4389-bd6b-8681c662e499/events" Name="Events" Type="SystemSessionEvents" Rel="Down"/>     </Links>     <SessionType>CatalogReplicationJob</SessionType>     <CreationTimeUTC>2025-01-30T16:38:54.377016Z</CreationTimeUTC>     <EndTimeUTC>2025-01-30T16:39:08.988371Z</EndTimeUTC>     <State>CompletedSuccessfully</State>     <Result>       <Result>CompletedSuccessfully</Result>       <Message/>       <IsCanceled>false</IsCanceled>     </Result>   </Sessions> </SystemSessions> |

Page updated 2026-07-29

