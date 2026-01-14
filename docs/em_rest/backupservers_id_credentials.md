---
title: "backupservers_id_credentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupservers_id_credentials.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <CredentialsInfoList xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
