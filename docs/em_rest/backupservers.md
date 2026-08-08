---
title: "/backupServers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupservers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupServers


Represents a collection of all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupServers |

Related Resources

[/backupServers/{ID}](backupservers_id.md)

Methods

The following methods are supported for the /backupServers resource:

* [GET /backupServers](get_backupservers.md)
* [POST /backupServers?action=create](post_backupservers.md)

Resource Representation

The /backupServers resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44" Name="srv03.tech.local" UID="urn:veeam:BackupServer:1eb5b858-e557-43b3-8e79-386161b7ea44">     <Links>       <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/jobs" />       <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/repositories" />       <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/credentials" />       <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/passwords" />       <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44?format=Entity" Name="srv03.tech.local" />       <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/managedServers" />     </Links>   </Ref>   <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b" Name="srv02.tech.local" UID="urn:veeam:BackupServer:6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b">     <Links>       <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/jobs" />       <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/repositories" />       <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/credentials" />       <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/passwords" />       <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b?format=Entity" Name="srv02.tech.local" />       <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/managedServers" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

