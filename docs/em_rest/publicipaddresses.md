---
title: "/cloud/publicIpAddresses"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/publicipaddresses.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/publicIpAddresses


Represents a collection of all public IP addresses allocated in the service provider's network infrastructure added to pools of public IP addresses on backup servers connected to Veeam Backup Enterprise Manager. Public IP addresses can be assigned to tenants. Tenants can use public IP addresses to enable access to cloud VM replicas from the internet after full site failover.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses |

Related Resources

[/cloud/publicIpAddresses/{ID}](publicipaddresses_id.md)

Methods

The following methods are supported for the /cloud/publicIpAddresses resource:

* [GET /cloud/publicIpAddresses](get_publicipaddresses.md)
* [POST /cloud/publicIpAddresses](post_publicipaddresses.md)

Resource Representation

The /cloud/publicIpAddresses resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/936db979-efbe-4ece-b279-07e24b4ea25e" Name="198.51.100.4" UID="urn:veeam:CloudPublicIpAddress:936db979-efbe-4ece-b279-07e24b4ea25e">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/936db979-efbe-4ece-b279-07e24b4ea25e?format=Entity" Name="198.51.100.4" />     </Links>   </Ref>   <Ref Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/11eebb50-5848-42a3-88cd-4932a5c8c894" Name="198.51.100.3" UID="urn:veeam:CloudPublicIpAddress:11eebb50-5848-42a3-88cd-4932a5c8c894">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/11eebb50-5848-42a3-88cd-4932a5c8c894?format=Entity" Name="198.51.100.3" />     </Links>   </Ref>   <Ref Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/fcf28ea0-6831-46ac-9abb-584e83a818ab" Name="198.51.100.9" UID="urn:veeam:CloudPublicIpAddress:fcf28ea0-6831-46ac-9abb-584e83a818ab">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/fcf28ea0-6831-46ac-9abb-584e83a818ab?format=Entity" Name="198.51.100.9" />     </Links>   </Ref>   <Ref Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/45a2c7c1-232b-4a1d-814e-59db3b1329c4" Name="198.51.100.8" UID="urn:veeam:CloudPublicIpAddress:45a2c7c1-232b-4a1d-814e-59db3b1329c4">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/45a2c7c1-232b-4a1d-814e-59db3b1329c4?format=Entity" Name="198.51.100.8" />     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

