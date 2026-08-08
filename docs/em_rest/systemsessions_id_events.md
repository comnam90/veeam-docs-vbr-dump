---
title: "/systemSessions/{ID}/events"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/systemsessions_id_events.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /systemSessions/{ID}/events


Represents a list of all log events of a system session having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/systemSessions/{ID}/events |

Related Resources

[/systemSessions/{ID}](systemsessions_id.md)

Methods

The following methods are supported for the /systemSessions/{ID}/events resource:

[GET /systemSessions/{ID}/events](get_systemsessions_id_events.md)

Resource Representation

The /systemSessions/{ID}/events resource has a resource representation of the following type:

|  |
| --- |
| <SystemSessionEvents xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25/events" Type="SystemSessionEvents">   <Links>     <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25?format=Entity" Name="Collect Job @2025-01-27 17:05:52.069837" Type="BackupJobSession" Rel="Up"/>   </Links>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.069837</CreationTimeUTC>     <Message>Starting data collection job...</Message>     <Order>1</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.101105</CreationTimeUTC>     <Message>Job successfully started.</Message>     <Order>2</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.101105</CreationTimeUTC>     <Message>Checking deleted backup servers removal</Message>     <Order>3</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.116682</CreationTimeUTC>     <Message>Preparing to collect data from enterprise05.tech.local</Message>     <Order>4</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.116682</CreationTimeUTC>     <Message>Retrieving data from enterprise05.tech.local...</Message>     <Order>5</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:06:10.30038</CreationTimeUTC>     <Message>Data collection from enterprise05.tech.local completed successfully.</Message>     <Order>6</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:06:10.488816</CreationTimeUTC>     <Message>Data collection job finished.</Message>     <Order>7</Order>   </Events> </SystemSessionEvents> |

Page updated 2026-07-29

