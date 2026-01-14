---
title: "cloudfailoverplans_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudfailoverplans_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a cloud failover plan that has the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cloud/cloudFailoverPlans](cloudfailoverplans.md)
* [/cloud/tenants/{ID}](tenants_id.md)

Methods

The following methods are supported for the /cloud/cloudFailoverPlans/{ID} resource:

* [GET /cloud/cloudFailoverPlans/{ID}](get_cloudfailoverplans_id.md)
* [PUT /cloud/cloudFailoverPlans/{ID}](put_cloudfailoverplans_id.md)
* [POST /cloud/cloudFailoverPlans/{ID}?action=start](post_cloudfailoverplans_id_start.md)
* [POST /cloud/cloudFailoverPlans/{ID}?action=undo](post_cloudfailoverplans_id_undo.md)
* [DELETE /cloud/cloudFailoverPlans/{ID}](delete_cloudfailoverplans_id.md)

Resource Representation

The /cloud/cloudFailoverPlans/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="FailoverPlanReference" Href="https://localhost:9398/api/managedServers/e7ca6822-a87f-443d-8aae-8005970543bf" Name="ABC Company Failover Plan" UID="urn:veeam:FailoverPlan:e7ca6822-a87f-443d-8aae-8005970543bf"> |

Entity resource representation:

|  |
| --- |
| <CloudFailoverPlan xmlns="http://www.veeam.com/ent/v1.0" Type="CloudFailoverPlan" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf?format=Entity" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverPlan:e7ca6822-a87f-443d-8aae-8005970543bf">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />     <Link Rel="Alternate" Type="CloudFailoverPlanReference" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf" Name="ABC Company Failover Plan" />     <Link Rel="Edit" Type="CloudFailoverPlanReference" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf" Name="ABC Company Failover Plan" />     <Link Rel="Start" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf?action=start" />     <Link Rel="Test" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf?action=test" />     <Link Rel="Undo" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf?action=undo" />     <Link Rel="Delete" Type="CloudFailoverPlanReference" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf" Name="ABC Company Failover Plan" />   </Links>   <TenantUid>urn:veeam:CloudTenant:b25f5f1d-a3c3-45ed-af23-9ef31a94dac7</TenantUid>   <TenantName>ABC Company</TenantName>   <Description>Cloud failover plan for ABC Company full site failover</Description>   <CloudFailoverPlanOptions>     <PostFailoverPlanCommandEnabled>false</PostFailoverPlanCommandEnabled>     <PostFailoverPlanCommand />     <PreFailoverPlanCommandEnabled>false</PreFailoverPlanCommandEnabled>     <PreFailoverPlanCommand />   </CloudFailoverPlanOptions>   <CloudFailoverPlanInfo>     <Includes>       <CloudFailoverPlanVm Type="CloudFailoveredVm" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf/includes/231a6e3e-09e6-4641-9322-40898fcb966a">         <FailoverPlanVMId>231a6e3e-09e6-4641-9322-40898fcb966a</FailoverPlanVMId>         <Name>srv38</Name>         <Order>0</Order>       </CloudFailoverPlanVm>       <CloudFailoverPlanVm Type="CloudFailoveredVm" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf/includes/096a7d0a-c92a-4da4-9302-4416b2fe929f">         <FailoverPlanVMId>096a7d0a-c92a-4da4-9302-4416b2fe929f</FailoverPlanVMId>         <Name>srv40</Name>         <Order>1</Order>       </CloudFailoverPlanVm>     </Includes>   </CloudFailoverPlanInfo> </CloudFailoverPlan> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
