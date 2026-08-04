---
title: "/cloud/tenants/{ID}/gatewayPools"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_gatewaypools.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/tenants/{ID}/gatewayPools


Represents a list of cloud gateway pools assigned for the tenant account with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/gatewayPools |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cloud/tenants/{ID}](tenants_id.md)
* [/cloud/gatewayPools](cloudgatewaypools.md)
* [/cloud/gatewayPools/{ID}](cloud_gatewaypools_id.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/gatewayPools resource:

[GET /cloud/tenants/{ID}/gatewayPools](get_cloud_tenants_id_gatewaypools.md)

Resource Representation

The /cloud/tenants/{ID}/gatewayPools resource has a resource representation of the following type.

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <Ref UID="urn:veeam:CloudGatewayPool:6de18dab-3341-441e-9184-a866913444d4" Name="Cloud gateway pool 1" Href="https://localhost:9398/api/cloud/gatewayPools/6de18dab-3341-441e-9184-a866913444d4" Type="CloudGatewayPoolReference">    <Links>      <Link Href="https://localhost:9398/api/backupServers/32ec2857-6c5a-4964-8486-061ba18fd6cf" Name="localhost" Type="BackupServerReference" Rel="Up"/>      <Link Href="https://localhost:9398/api/cloud/gatewayPools/6de18dab-3341-441e-9184-a866913444d4?format=Entity" Name="Cloud gateway pool 1" Type="CloudGatewayPool"Rel="Alternate"/>    </Links>  </Ref> </EntityReferences> |

Page updated 2026-07-29

