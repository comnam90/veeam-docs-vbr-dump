---
title: "/failoverPlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/failoverplans.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /failoverPlans


Represents a collection of failover plans configured on backup servers that are connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Note |
| The /failoverPlans resource represents only regular failover plans configured on a backup server managed by Veeam Backup Enterprise Manager. Cloud failover plans configured by tenants whose accounts are created on a backup server appear in the /cloud/cloudFailoverPlans resource representation. |

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/failoverPlans |

Related Resources

[/failoverPlans/{ID}](failoverplans_id.md)

Methods

The following methods are supported for the /failoverPlans resource:

[GET /failoverPlans](get_failover_plans.md)

Resource Representation

The /failoverPlans resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009" Name="SQL Failover Plan" UID="urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="FailoverPlan" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009?format=Entity" Name="SQL Failover Plan" />     </Links>   </Ref>   <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/failoverPlans/8c6ac2a1-8330-400e-9194-40310b5ca58a" Name="Exchange Group Failover Plan" UID="urn:veeam:FailoverPlan:8c6ac2a1-8330-400e-9194-40310b5ca58a">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="FailoverPlan" Href="https://localhost:9398/api/failoverPlans/8c6ac2a1-8330-400e-9194-40310b5ca58a?format=Entity" Name="Exchange Group Failover Plan" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

