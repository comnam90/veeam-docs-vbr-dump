---
title: "/backupServers/{ID}/passwords/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupservers_id_passwords_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /backupServers/{ID}/passwords/{ID}


Represents a password with the specified ID created on the backup server with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupServers/{ID}/passwords/{ID} |

Related Resources

[/backupServers](backupservers.md)

Methods

The following methods are supported for the /backupServers/{ID}/passwords/{ID} resource:

* [GET /backupServers/{ID}/passwords/{ID}](get_backupservers_id_passwords_id.md)
* [PUT /backupServers/{ID}/passwords/{ID}](put_backupservers_id_passwords_id.md)
* [DELETE /backupServers/{ID}/passwords/{ID}](delete_backupservers_id_passwords_id.md)

Resource Representation

The /backupServers/{ID}/passwords/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <PasswordKeyInfo xmlns="http://www.veeam.com/ent/v1.0" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/cacd84ea-5cc9-46b5-9e79-2162c4170662"> |


