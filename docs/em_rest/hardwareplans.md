---
title: "/cloud/hardwarePlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/hardwareplans.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/hardwarePlans


Represents a collection of all hardware plans configured on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans |

Related Resources

[/cloud/hardwarePlans/{ID}](hardwareplans_id.md)

Methods

The following methods are supported for the /cloud/hardwarePlans resource:

* [GET /cloud/hardwarePlans](get_hardwareplans.md)
* [POST /cloud/hardwarePlans](post_hardwareplans.md)

Resource Representation

The /cloud/hardwarePlans resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536" Name="Hyper-V Silver" UID="urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536?format=Entity" Name="Hyper-V Silver" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/ed6ad5f1-671b-4875-9d81-72a431953aca" Name="VMware Bronze" UID="urn:veeam:CloudHardwarePlan:ed6ad5f1-671b-4875-9d81-72a431953aca">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/ed6ad5f1-671b-4875-9d81-72a431953aca?format=Entity" Name="VMware Bronze" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/7dc3ffa1-78a0-46a2-b098-9720c40c9915" Name="VMware Gold" UID="urn:veeam:CloudHardwarePlan:7dc3ffa1-78a0-46a2-b098-9720c40c9915">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/7dc3ffa1-78a0-46a2-b098-9720c40c9915?format=Entity" Name="VMware Gold" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/d2d37ef0-dc9d-43b4-9fa4-b4e850fab171" Name="Hyper-V Gold" UID="urn:veeam:CloudHardwarePlan:d2d37ef0-dc9d-43b4-9fa4-b4e850fab171">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/d2d37ef0-dc9d-43b4-9fa4-b4e850fab171?format=Entity" Name="Hyper-V Gold" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/91156f8d-8bd3-44af-bec3-b6ac2ea24288" Name="VMware Silver" UID="urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/91156f8d-8bd3-44af-bec3-b6ac2ea24288?format=Entity" Name="VMware Silver" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/82951b35-4581-4610-983a-e3a12aea1a8e" Name="Hyper-V Bronze" UID="urn:veeam:CloudHardwarePlan:82951b35-4581-4610-983a-e3a12aea1a8e">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/82951b35-4581-4610-983a-e3a12aea1a8e?format=Entity" Name="Hyper-V Bronze" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

