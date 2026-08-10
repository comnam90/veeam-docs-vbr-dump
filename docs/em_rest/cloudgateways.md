---
title: "/cloud/gateways"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudgateways.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/gateways


Represents a collection of cloud gateways configured on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/gateways |

Related Resources

[/cloud/gateways/{ID}](cloudgateways_id.md)

Methods

The following methods are supported for the /cloud/gateways resource:

* [GET /cloud/gateways](get_cloudgateways.md)
* [POST /cloud/gateways](post_gateways.md)

Resource Representation

The /cloud/gateways resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudGatewayReference" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd" Name="172.16.13.97" UID="urn:veeam:CloudGateway:b5025a7b-5e13-41e2-a17e-9d9af985ecfd">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd?format=Entity" Name="172.16.13.97" />     </Links>   </Ref>   <Ref Type="CloudGatewayReference" Href="https://localhost:9398/api/cloud/gateways/cc79315a-2313-4360-a72a-e3b4d73f1288" Name="172.16.13.119" UID="urn:veeam:CloudGateway:cc79315a-2313-4360-a72a-e3b4d73f1288">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/cc79315a-2313-4360-a72a-e3b4d73f1288?format=Entity" Name="172.16.13.119" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

