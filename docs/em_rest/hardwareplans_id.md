---
title: "/cloud/hardwarePlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/hardwareplans_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/hardwarePlans/{ID}


Represents a hardware plan that has the specified ID.

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans/{ID}?format=Entity |

Related Resources

[/cloud/hardwarePlans](hardwareplans.md)

[/cloud/hardwarePlans/{ID}/tenants](hardwareplans_id_tenants.md)

Methods

The following methods are supported for the /cloud/hardwarePlans/{ID} resource:

* [GET /cloud/hardwarePlans/{ID}](get_hardwareplans_id.md)
* [PUT /cloud/hardwarePlans/{ID}](put_hardwareplans_id.md)
* [DELETE /cloud/hardwarePlans/{ID}](delete_hardwareplans_id.md)

Resource Representation

The /cloud/hardwarePlans/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536" Name="Hyper-V Silver" UID="urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536"> |

Entity resource representation:

|  |
| --- |
| <CloudHardwarePlan xmlns="http://www.veeam.com/ent/v1.0" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536?format=Entity" Name="Hyper-V Silver" UID="urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />     <Link Rel="Alternate" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536" Name="Hyper-V Silver" />     <Link Rel="Down" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536/tenants" Name="Hyper-V Silver" />     <Link Rel="Edit" Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536" Name="Hyper-V Silver" />     <Link Rel="Delete" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536" Name="Hyper-V Silver" />   </Links>   <Description>Hardware plan for Hyper-V VMs</Description>   <ProcessorUsageLimitMhz>10000</ProcessorUsageLimitMhz>   <MemoryUsageLimitMb>16384</MemoryUsageLimitMb>   <HardwarePlanDetails>     <HvCloudHardwarePlan>       <HypervisorHostRef>urn:HyperV:Host:849a937a-3416-4f03-8111-67b06393afcb.</HypervisorHostRef>       <Volumes>         <Volume Id="66d75e14-a35a-4dfe-a919-9b2a3bf87e4a">           <FriendlyName>Cloud Replicas</FriendlyName>           <VolumePath>D:\Replicas</VolumePath>           <QuotaGb>300</QuotaGb>         </Volume>       </Volumes>       <Network Id="127e652e-e02e-4951-99e7-03280edfe536">         <CountWithInternet>1</CountWithInternet>         <CountWithoutInternet>1</CountWithoutInternet>       </Network>     </HvCloudHardwarePlan>   </HardwarePlanDetails> </CloudHardwarePlan> |


