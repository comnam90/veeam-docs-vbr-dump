---
title: "/cloud/gatewayPools"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudgatewaypools.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/gatewayPools


Represents a collection of cloud gateway pools configured on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/gatewayPools |

Related Resources

[/cloud/gatewayPools/{ID}](cloud_gatewaypools_id.md)

Methods

The following methods are supported for the /cloud/gatewayPools resource:

* [GET /cloud/gatewayPools](get_cloudgatewaypools.md)
* [POST /cloud/gatewayPools](post_cloudgatewaypools.md)

Resource Representation

The /cloud/gatewayPools resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:CloudGatewayPool:6de18dab-3341-441e-9184-a866913444d4" Name="Cloud gateway pool 1" Href="http://local.host:9399/api/cloud/gatewayPools/6de18dab-3341-441e-9184-a866913444d4" Type="CloudGatewayPoolReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/cloud/gatewayPools/6de18dab-3341-441e-9184-a866913444d4?format=Entity" Name="Cloud gateway pool 1" Type="CloudGatewayPool" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

