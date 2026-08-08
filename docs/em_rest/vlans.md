---
title: "/cloud/vlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vlans.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/vlans


Represents a collection of all virtual switches on which VLAN ranges for Veeam Cloud Connect Replication are reserved. VLANs are used for providing networking capabilities to tenant VM replicas. Virtual switches are configured on virtualization hosts that are used as a replication target and connected to backup servers managed by Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/vlans |

Related Resources

[/cloud/vlans/{ID}](vlans_id.md)

Methods

The following methods are supported for the /cloud/vlans resource:

[GET /cloud/vlans](get_vlans.md)

Resource Representation

The /cloud/vlans resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533" Name="vSwitch0" UID="urn:veeam:VlanConfiguration:78c6a038-38a2-4908-ac19-1540f9448533">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="VlanConfiguration" Href="https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533?format=Entity" Name="vSwitch0" />     </Links>   </Ref>   <Ref Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/510f34ea-1534-437c-a746-f32cf0f712aa" Name="Intel(R) I350 Gigabit Network Connection - Virtual Switch" UID="urn:veeam:VlanConfiguration:510f34ea-1534-437c-a746-f32cf0f712aa">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="VlanConfiguration" Href="https://localhost:9398/api/cloud/vlans/510f34ea-1534-437c-a746-f32cf0f712aa?format=Entity" Name="Intel(R) I350 Gigabit Network Connection - Virtual Switch" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

