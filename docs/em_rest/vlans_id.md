---
title: "/cloud/vlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vlans_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/vlans/{ID}


Represents a virtual switch with the specified ID on which VLAN ranges for Veeam Cloud Connect Replication are reserved. VLANs are used for providing networking capabilities to tenant VM replicas. The virtual switch is configured on the virtualization host that is used as a replication target and connected to the backup server managed by Veeam Backup Enterprise Manager.

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/vlans/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/vlans/{ID}?format=Entity |

Related Resources

[/cloud/vlans](vlans.md)

Methods

The following methods are supported for the /cloud/vlans/{ID} resource:

* [GET /cloud/vlans/{ID}](get_vlans_id.md)
* [PUT /cloud/vlans/{ID}](put_vlans_id.md)
* [DELETE /cloud/vlans/{ID}](delete_vlans_id.md)

Resource Representation

The /cloud/vlans/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533" Name="vSwitch0" UID="urn:veeam:VlanConfiguration:78c6a038-38a2-4908-ac19-1540f9448533"> |

Entity resource representation:

|  |
| --- |
| <VlanConfiguration xmlns="http://www.veeam.com/ent/v1.0" Name="vSwitch0" UID="78c6a038-38a2-4908-ac19-1540f9448533">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />     <Link Rel="Alternate" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533" Name="vSwitch0" />     <Link Rel="Edit" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533" Name="vSwitch0" />     <Link Rel="Delete" Type="VlanConfiguration" Href="https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533" Name="vSwitch0" />   </Links>   <HostRef>urn:VMware:Host:4a3f28d9-d4f3-4e4c-9afb-91db8ab57436.host-438</HostRef>   <PlatformType>VMware</PlatformType>   <VlanIdsWithInternetLeftBound>500</VlanIdsWithInternetLeftBound>   <VlanIdsWithInternetRightBound>510</VlanIdsWithInternetRightBound>   <VlanIdsWithoutInternetLeftBound>511</VlanIdsWithoutInternetLeftBound>   <VlanIdsWithoutInternetRightBound>520</VlanIdsWithoutInternetRightBound>   <SwitchName>vSwitch0</SwitchName>   <SwitchId>vSwitch0</SwitchId>   <SwitchType>VirtualSwitch</SwitchType> </VlanConfiguration> |


