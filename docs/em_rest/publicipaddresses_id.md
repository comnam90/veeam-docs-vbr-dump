---
title: "/cloud/publicIpAddresses/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/publicipaddresses_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a public IP address with the specified ID. Public IP address is added to the pool of public IP addresses on the backup server connected to Veeam Backup Enterprise Manager.

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses/{ID}?format=Entity |

Related Resources

[/cloud/publicIpAddresses](publicipaddresses.md)

Methods

The following methods are supported for the /cloud/publicIpAddresses/{ID} resource:

* [GET /cloud/publicIpAddresses/{ID}](get_publicipaddresses_id.md)
* [PUT /cloud/publicIpAddresses/{ID}](delete_publicipaddresses_id.md)
* [DELETE /cloud/publicIpAddresses/{ID}](delete_publicipaddresses_id.md)

Resource Representation

The /cloud/publicIpAddresses/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648" Name="198.51.100.16" UID="urn:veeam:CloudPublicIpAddress:22d2cdad-ddd1-4789-9e27-03bf25786648"> |

Entity resource representation:

|  |
| --- |
| <CloudPublicIpAddress xmlns="http://www.veeam.com/ent/v1.0" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648?format=Entity" Name="198.51.100.16" UID="urn:veeam:CloudPublicIpAddress:22d2cdad-ddd1-4789-9e27-03bf25786648" BackupServerUid="urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />     <Link Rel="Alternate" Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648" Name="198.51.100.16" />     <Link Rel="Edit" Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648" Name="198.51.100.16" />     <Link Rel="Delete" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648" Name="198.51.100.16" />   </Links>   <IpAddress>198.51.100.16</IpAddress> </CloudPublicIpAddress> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
