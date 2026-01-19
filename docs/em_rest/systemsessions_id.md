---
title: "/systemSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/systemsessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /systemSessions/{ID}


Represents a system session having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/systemSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/systemSessions/{ID}?format=Entity |

Related Resources

[/systemSessions](systemsessions.md)

Methods

The following methods are supported for the /systemSessions/{ID} resource:

[GET /systemSessions/{ID}](get_systemsessions_id.md)

Resource Representation

The /systemSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

Entity resource representation:

|  |
| --- |
| <SystemSession xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25?format=Entity" Type="SystemSession" Name="Collect Job @2023-01-27 17:05:52.069837" UID="urn:veeam:SystemSession:00057ade-8f1a-4b54-a265-391441981e25">   <Links>     <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25" Name="Collect Job @2023-01-27 17:05:52.069837" Type="BackupJobSessionReference" Rel="Alternate"/>     <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25/events" Name="Events" Type="SystemSessionEvents" Rel="Down"/>   </Links>   <SessionType>CollectJob</SessionType>   <CreationTimeUTC>2023-01-27T17:05:52.069837Z</CreationTimeUTC>   <EndTimeUTC>2023-01-27T17:06:10.491337Z</EndTimeUTC>   <State>CompletedSuccessfully</State>   <Result>     <Result>CompletedSuccessfully</Result>     <Message/>     <IsCanceled>false</IsCanceled>   </Result> </SystemSession> |


