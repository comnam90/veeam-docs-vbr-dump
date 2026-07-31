---
title: "/cloud/replicas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudreplicas.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/replicas


Represents a collection of replicas created by tenants whose accounts are created on all backup servers connected to Veeam Backup Enterprise Manager.

The collection includes the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/replicas |

Related Resources

[/cloud/replicas/{ID}](cloudreplicas_id.md)

Methods

The following methods are supported for the /cloud/replicas resource:

[GET /cloud/replicas](get_cloudreplicas.md)

Resource Representation

The /cloud/replicas resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" UID="urn:veeam:CloudReplica:8393c284-c953-403f-a9b9-cff63e0c6815">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815?format=Entity" Name="ABC Company Servers Replication" />       <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/vmReplicaPoints/8393c284-c953-403f-a9b9-cff63e0c6815/vmReplicaPoints" />     </Links>   </Ref>   <Ref Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/6b2b42d5-3850-421c-93c1-e063f12a2ead" Name="UCM Company CRM Replication" UID="urn:veeam:CloudReplica:6b2b42d5-3850-421c-93c1-e063f12a2ead">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/6b2b42d5-3850-421c-93c1-e063f12a2ead?format=Entity" Name="UCM Company CRM Replication" />       <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/vmReplicaPoints/6b2b42d5-3850-421c-93c1-e063f12a2ead/vmReplicaPoints" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

