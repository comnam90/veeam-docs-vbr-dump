---
title: "GET /backupServers/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupservers_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of the backup server having the specified ID.

Request

To get a resource representation of the backup server, send the GET HTTP request to the /backupServers/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupservers/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupServers/{ID}?format=Entity |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /backupServers/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the backup server connected to Veeam Backup Enterprise Manager, for example: urn:veeam:BackupServer:15942270-fb56-4dcc-96e9-5f80e4725a15. |
| Name | String | Name of the backup server connected to Veeam Backup Enterprise Manager, for example: Backup Server 1. |
| Description | String | Description specified for the backup server in Veeam Backup Enterprise Manager. |
| Port | Int64 | Port used by Veeam Backup Enterprise Manager for collecting data from backup servers. By default, port 9392 is used. |
| Version | String | Version of Veeam Backup & Replication installed on the backup server, for example: 13.0.0.1420. |
| WcfPort | UShort | Default certificate port used by Veeam Backup Enterprise Manager for collecting data from backup servers that have Veeam Backup & Replication 12 or later installed, for example: 9405. |
| VbrCertificateThumbprint | String | Certificate thumbprint of the backup server, for example: 0000000000000000000000000000000000000000. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=BackupServer](get_query_backupserver.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Alternate | Alternate URL of the [/backupServers/{ID}](backupservers_id.md) resource. |
| /backupServers/{ID} | Edit | URL for the [PUT /backupServers/{ID}](put_backupservers_id.md) request. |
| /backupServers/{ID} | Delete | URL for the [DELETE /backupServers/{ID}](delete_backupservers_id.md) request. |
| /backupServers/{ID}/jobs | Down | URL of the [/jobs](jobs.md) resource — a collection of jobs configured on the backup server. |
| /backupServers/{ID}/managedServers | Down | URL of the [/managedServers](managedservers.md) resource — a collection of managed servers added to the backup server infrastructure. |
| /backupServers/{ID}/repositories | Down | URL of the [/repositories](repositories.md) resource — a collection of repositories configured on the backup server. |
| /backupServers/{ID}/externalRepositories | Down | URL of the [/externalRepositories](externalrepositories.md) resource — a collection of external repositories configured on the backup server. |
| /backupServers/{ID}/credentials | Down | URL of the [/backupServers/{ID}/credentials](backupservers_id_credentials.md) resource — a collection of credentials created on the backup server. |
| /backupServers/{ID}/credentials?action=create | Create | URL for the [POST /backupServers/{ID}/credentials?action=create](post_backupservers_id_creds.md) request. |
| /backupServers/{ID}/passwords | Down | URL of the [/backupServers/{ID}/passwords](backupservers_id_passwords.md) resource — a collection of passwords created on the backup server. |
| /backupServers/{ID}/passwords?action=create | Create | URL for the [POST /backupServers/{ID}/passwords?action=create](post_backupservers_id_passwords.md) request. |
| /backupServers/{ID}?action=veeamzip | VeeamZip | URL for the [POST /backupServers/{ID}?action=veeamzip](post_backupservers_id_zip.md) request. |
| /backupServers/{ID}?action=quickbackup | QuickBackup | URL for the [POST /backupServers/{ID}?action=quickbackup](post_backupservers_id_quickbackup.md) request. |
| /backupServers/{ID}?action=collect | Start | URL for the [POST /backupServers/{ID}?action=collect](post_backupservers_id_collect.md) request. |

Example

The example below returns an entity representation of the backup server having ID 838b99f7-88c0-4832-b6ab-3ac8a935d058.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupServers/838b99f7-88c0-4832-b6ab-3ac8a935d058?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
