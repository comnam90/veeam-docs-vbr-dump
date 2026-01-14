---
title: "cloudfailoversessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudfailoversessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a cloud failover session that has the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/failoverSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/failoverSessions/{ID}?format=Entity |

Related Resources

[/cloud/failoverSessions](cloudfailoversessions.md)

Methods

The following methods are supported for the /cloud/failoverSessions/{ID} resource:

[GET /cloud/failoverSessions/{ID}](get_cloudfailoversessions_id.md)

Resource Representation

The /cloud/failoverSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/475420ee-d045-4493-9869-0a970e08f6f9" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverSession:475420ee-d045-4493-9869-0a970e08f6f9"> |

Entity resource representation:

|  |
| --- |
| <CloudFailoverSession xmlns="http://www.veeam.com/ent/v1.0" Type="CloudFailoverSession" Href="https://localhost:9398/api/cloud/failoverSessions/475420ee-d045-4493-9869-0a970e08f6f9?format=Entity" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverSession:475420ee-d045-4493-9869-0a970e08f6f9">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />     <Link Rel="Alternate" Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/475420ee-d045-4493-9869-0a970e08f6f9" Name="ABC Company Failover Plan" />   </Links>   <JobType>FailoverPlan</JobType>   <CreationTimeUTC>2015-12-07T17:38:16Z</CreationTimeUTC>   <EndTimeUTC>2015-12-07T17:39:36Z</EndTimeUTC>   <State>Stopped</State>   <Result>Success</Result>   <Progress>100</Progress>   <CloudFailoverTasks /> </CloudFailoverSession> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
