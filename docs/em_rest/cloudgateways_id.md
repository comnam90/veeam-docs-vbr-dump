---
title: "/cloud/gateways/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudgateways_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/gateways/{ID}


Represents a cloud gateway having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/gateways/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/gateways/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id_credentials.md)
* [/cloud/gateways](cloudgateways.md)

Methods

The following methods are supported for the /cloud/gateways/{ID} resource:

* [GET /cloud/gateways/{ID}](get_cloudgateways_id.md)
* [PUT /cloud/gateways/{ID}](put_cloudgateways_id.md)
* [DELETE /cloud/gateways/{ID}](delete_cloudgateways_id.md)

Resource Representation

The /cloud/gateways/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CloudGatewayReference" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd" Name="172.16.13.97" UID="urn:veeam:CloudGateway:b5025a7b-5e13-41e2-a17e-9d9af985ecfd"> |

Entity resource representation:

|  |
| --- |
| <CloudGateway xmlns="http://www.veeam.com/ent/v1.0" Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd?format=Entity" Name="172.16.13.97" UID="urn:veeam:CloudGateway:b5025a7b-5e13-41e2-a17e-9d9af985ecfd">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />     <Link Rel="Alternate" Type="CloudGatewayReference" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd" Name="172.16.13.97" />     <Link Rel="Edit" Type="CloudGatewayReference" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd" Name="172.16.13.97" />     <Link Rel="Delete" Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd" Name="172.16.13.97" />   </Links>   <Enabled>true</Enabled>   <NetworkMode>Direct</NetworkMode>   <ExternalIP>172.16.13.97</ExternalIP>   <ExternalPort>6180</ExternalPort>   <InternalPort>6180</InternalPort>   <Description>Cloud gateway 1</Description> </CloudGateway> |


