---
title: "/cloud/cloudFailoverPlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudfailoverplans.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/cloudFailoverPlans


Represents a collection of cloud failover plans configured by tenants on backup servers that are connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans |

Related Resources

[/cloud/cloudFailoverPlans/{ID}](cloudfailoverplans_id.md)

Methods

The following methods are supported for the /cloud/cloudFailoverPlans resource:

[GET cloud/cloudFailoverPlans](get_cloudfailoverplans.md)

Resource Representation

The /cloud/cloudFailoverPlans resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/managedServers/e7ca6822-a87f-443d-8aae-8005970543bf" Name="ABC Company Failover Plan" UID="urn:veeam:FailoverPlan:e7ca6822-a87f-443d-8aae-8005970543bf">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverPlan" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf?format=Entity" Name="ABC Company Failover Plan" />       <Link Rel="Related" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7?format=Entity" Name="ABC Company" />     </Links>   </Ref>   <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/managedServers/08d5bbf5-619b-4bb9-ba51-95f4678544f4" Name="UCM Company Full SIte Failover" UID="urn:veeam:FailoverPlan:08d5bbf5-619b-4bb9-ba51-95f4678544f4">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverPlan" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/08d5bbf5-619b-4bb9-ba51-95f4678544f4?format=Entity" Name="UCM Company Full SIte Failover" />       <Link Rel="Related" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6?format=Entity" Name="UCM Company" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

