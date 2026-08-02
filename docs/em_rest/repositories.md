---
title: "/repositories"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/repositories.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /repositories


Represents a collection of all backup repositories created on backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/repositories |

Related Resources

[/repositories/{ID}](repositories_id.md)

Methods

The following methods are supported for the /repositories resource:

[GET /repositories](get_repositories.md)

Resource Representation

The /repositories resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   </Ref>   <Ref Type="RepositoryReference" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6" Name="Backup Volume 01" UID="urn:veeam:Repository:bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Repository" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6?format=Entity" Name="Backup Volume 01" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6/backups" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6/replicas" />     </Links>   </Ref>   <Ref Type="RepositoryReference" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55" Name="Default Backup Repository" UID="urn:veeam:Repository:cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Repository" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55?format=Entity" Name="Default Backup Repository" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55/backups" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55/replicas" />     </Links>   </Ref>   <Ref Type="RepositoryReference" Href="https://localhost:9398/api/repositories/eed5ff37-79f4-4d2b-bad6-7c82b399ba61" Name="Alpha Repository" UID="urn:veeam:Repository:eed5ff37-79f4-4d2b-bad6-7c82b399ba61">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Repository" Href="https://localhost:9398/api/repositories/eed5ff37-79f4-4d2b-bad6-7c82b399ba61?format=Entity" Name="Alpha Repository" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/eed5ff37-79f4-4d2b-bad6-7c82b399ba61/backups" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/eed5ff37-79f4-4d2b-bad6-7c82b399ba61/replicas" />     </Links>   </Ref>   <Ref Type="RepositoryReference" Href="https://localhost:9398/api/repositories/98fbd079-f5ae-48f8-8ec2-e148333fef93" Name="Omega Cloud Vol1" UID="urn:veeam:Repository:98fbd079-f5ae-48f8-8ec2-e148333fef93">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Repository" Href="https://localhost:9398/api/repositories/98fbd079-f5ae-48f8-8ec2-e148333fef93?format=Entity" Name="Omega Cloud Vol1" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/98fbd079-f5ae-48f8-8ec2-e148333fef93/backups" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/98fbd079-f5ae-48f8-8ec2-e148333fef93/replicas" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

