---
title: "/backupServers/{ID}/credentials/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupservers_id_creds_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /backupServers/{ID}/credentials/{ID}


Represents a credentials record with the specified ID created on the backup server with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupServers/{ID}/credentials/{ID} |

Related Resources

[/backupServers](backupservers.md)

Methods

The following methods are supported for the /backupServers/{ID}/credentials/{ID} resource:

* [GET /backupServers/{ID}/credentials/{ID}](get_backupservers_id_creds_id.md)
* [PUT /backupServers/{ID}/credentials/{ID}](put_backupservers_id_creds_id.md)
* [DELETE /backupServers/{ID}/credentials/{ID}](delete_backupservers_id_creds_id.md)

Resource Representation

The /backupServers/{ID}/credentials/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <CredentialsInfo xmlns="http://www.veeam.com/ent/v1.0" Type="Credentials" Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/credentials/70275b03-e805-49e1-9535-1867c62371e2"> |


