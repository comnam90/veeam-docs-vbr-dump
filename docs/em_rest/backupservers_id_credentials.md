---
title: "/backupServers/{ID}/credentials"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupservers_id_credentials.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupServers/{ID}/credentials


Represents a collection of credentials created on the backup server having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupServers/{ID}/credentials |

Related Resources

[/backupServers/{ID}/credentials/{ID}](backupservers_id_creds_id.md)

Methods

The following methods are supported for the /backupServers/{ID}/credentials resource:

* [GET /backupServers/{ID}/credentials](get_backupservers_id_creds.md)
* [POST /backupServers/{ID}/credentials](post_backupservers_id_creds.md)

Resource Representation

The /backupServers/{ID}/credentials resource has a resource representation of the following type:

|  |
| --- |
| <CredentialsInfoList xmlns="http://www.veeam.com/ent/v1.0">    <CredentialsInfo Type="Credentials" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials/a45eb049-6f8d-49d4-9dba-4f1499f9d8d1">     <Links>       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c?format=Entity" Name="win-tw5" />       <Link Rel="Edit" Type="Credentials" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials/a45eb049-6f8d-49d4-9dba-4f1499f9d8d1" />       <Link Rel="Delete" Type="Credentials" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials/a45eb049-6f8d-49d4-9dba-4f1499f9d8d1" />     </Links>     <Id>a45eb049-6f8d-49d4-9dba-4f1499f9d8d1</Id>     <Username>root</Username>     <Description>Credentials for ESXi and Linux hosts.</Description>     <Password />   </CredentialsInfo>   <CredentialsInfo Type="Credentials" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials/d5e6816b-155d-4c2f-a555-4ad249fab682">     <Links>       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c?format=Entity" Name="win-tw5" />       <Link Rel="Edit" Type="Credentials" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials/d5e6816b-155d-4c2f-a555-4ad249fab682" />       <Link Rel="Delete" Type="Credentials" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials/d5e6816b-155d-4c2f-a555-4ad249fab682" />     </Links>     <Id>d5e6816b-155d-4c2f-a555-4ad249fab682</Id>     <Username>VEEAM\administrator</Username>     <Description>Credentials for virtual infrastructure servers</Description>     <Password />   </CredentialsInfo> </CredentialsInfoList> |

Page updated 2026-07-29

