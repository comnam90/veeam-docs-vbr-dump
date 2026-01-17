---
title: "/backupServers/{ID}/passwords"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupservers_id_passwords.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <PasswordKeyInfoList xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
