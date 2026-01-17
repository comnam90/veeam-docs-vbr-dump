---
title: "/cloud/gatewayPools/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloud_gatewaypools_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/gatewayPools/{ID}


Represents a cloud gateway pool with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/gatewayPools/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/gatewayPools/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cloud/tenants](tenants.md)
* [/cloud/gatewayPools](cloudgatewaypools.md)

Methods

The following methods are supported for the /cloud/gatewayPools/{ID} resource:

* [GET /cloud/gatewayPools/{ID}](get_cloud_gatewaypools_id.md)
* [PUT /cloud/gatewayPools/{ID}](put_cloud_gatewaypools_id.md)
* [DELETE /cloud/gatewayPools/{ID}](delete_cloud_gatewaypools_id.md)

Resource Representation

The /cloud/gatewayPools/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7" Name="ABC Company" UID="urn:veeam:CloudTenant:b25f5f1d-a3c3-45ed-af23-9ef31a94dac7"> |

Entity resource representation:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <CloudGatewayPool Href="https://localhost:9398/api/cloud/gatewayPools/64bf55fb-b53f-4214-950a-fcc3a241622b?format=Entity" Type="CloudGatewayPool" Name="GatewayPool 1" UID="urn:veeam:CloudGatewayPool:64bf55fb-b53f-4214-950a-fcc3a241622b" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="https://localhost:9398/api/backupServers/32ec2857-6c5a-4964-8486-061ba18fd6cf" Name="localhost" Type="BackupServerReference" Rel="Up"/>     <Link Href="https://localhost:9398/api/cloud/gatewayPools/64bf55fb-b53f-4214-950a-fcc3a241622b" Name="GatewayPool 1" Type="CloudGatewayPoolReference" Rel="Alternate"/>     <Link Href="https://localhost:9398/api/cloud/gatewayPools/64bf55fb-b53f-4214-950a-fcc3a241622b" Name="GatewayPool 1" Type="CloudGatewayPoolReference" Rel="Edit"/>     <Link Href="https://localhost:9398/api/cloud/gatewayPools/64bf55fb-b53f-4214-950a-fcc3a241622b" Rel="Delete"/>     <Link Href="https://localhost:9398/api/cloud/gatewayPools/64bf55fb-b53f-4214-950a-fcc3a241622b/gateways" Type="CloudGatewayReferenceList" Rel="Down"/>   </Links>   <Description>Created by REST API</Description>   <CloudGateways/>   <CloudTenants/> </CloudGatewayPool> |


