---
title: "/backupServers/{ID}/passwords"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupservers_id_passwords.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupServers/{ID}/passwords


Represents a collection of passwords created on the backup server having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupServers/{ID}/passwords |

Related Resources

[/backupServers/passwords{ID}](backupservers_id_passwords_id.md)

Methods

The following methods are supported for the /backupServers/{ID}/passwords resource:

* [GET /backupServers/{ID}/passwords](get_backupservers_id_passwords.md)
* [POST /backupServers/{ID}/passwords?action=create](post_backupservers_id_passwords.md)

Resource Representation

The /backupServers/{ID}/passwords resource has a resource representation of the following type:

|  |
| --- |
| <PasswordKeyInfoList xmlns="http://www.veeam.com/ent/v1.0">   <PasswordKeyInfo Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/cacd84ea-5cc9-46b5-9e79-2162c4170662">     <Links>       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?format=Entity" Name="srv02.tech.local" />       <Link Rel="Edit" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/cacd84ea-5cc9-46b5-9e79-2162c4170662" />       <Link Rel="Delete" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/cacd84ea-5cc9-46b5-9e79-2162c4170662" />     </Links>     <Id>cacd84ea-5cc9-46b5-9e79-2162c4170662</Id>     <Hint>My password</Hint>     <LastModificationDate>2025-10-10T23:06:17-08:00</LastModificationDate>   </PasswordKeyInfo>   <PasswordKeyInfo Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/3b39fed1-c9e8-46bf-be7e-2a096a210341">     <Links>       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?format=Entity" Name="srv02.tech.local" />       <Link Rel="Edit" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/3b39fed1-c9e8-46bf-be7e-2a096a210341" />       <Link Rel="Delete" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/3b39fed1-c9e8-46bf-be7e-2a096a210341" />     </Links>     <Id>3b39fed1-c9e8-46bf-be7e-2a096a210341</Id>     <Hint>My favorite book</Hint>     <LastModificationDate>2025-10-13T02:50:38-07:00</LastModificationDate>   </PasswordKeyInfo> </PasswordKeyInfoList> |

Page updated 2026-07-29

