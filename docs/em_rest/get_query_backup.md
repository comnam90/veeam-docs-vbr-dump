---
title: "get_query_backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_backup.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of backups created on or imported to backup servers connected to Veeam Backup Enterprise Manager. For details, see [/backups](backups.md).

Request

To get a list of backups, send the GET HTTP request to the query with the type parameter set to Backup.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=Backup |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the backup resource, for example: urn:veeam:Backup:58c917c7-7b7a-41ff-8676-226656c35c05. |
| Name | String | Name of the backup job parent to the backup, for example: SQL Backup. |
| JobUid | UidType | UID of the backup job parent to the backup, for example:urn:veeam:Job:da736815-4fea-4c8e-b0e1-5ecdbca1c512. |
| JobName | String | Name of the backup job parent to the backup, for example: DNS Backup. |
| RepositoryUid | UidType | UID of the backup repository parent to the backup, for example: urn:veeam:Repository:b609c947-dd30-4295-8b57-cc880329dbd6. |
| RepositoryName | Name | Name of the backup repository parent to the backup, for example: Backup Vol 1. |
| Platform | String | Type of a platform of a backup resource. Possible values:   * VMware — for protected VMware vSphere VMs. * HyperV — for protected Microsoft Hyper-V VMs. * vCloud — for protected VMware Cloud Director resources. * AgentForLinux — for machines protected with Veeam Agent for Linux. * AgentForWindows — for machines protected with Veeam Agent for Windows. * CustomPlatform — for Nutanix and other custom platforms. |
| BackupType | String | Type of a backup resource. Possible values:   * Standard — for VMware, HyperV, vCloud and Standalone Veeam Backup Agent backup resources. * ParentBackup — for backup container resources. Represents a backup created by a Veeam Agent backup job in the Veeam Agent Management scenario, and contains links for child backups. * ChildBackup — for backup resources that have links to restore points and parent backups. Represents a backup of a separate machine in the backup created by a Veeam Agent backup job in the Veeam Agent Management scenario. |

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

In the response body, the REST API returns a representation of the /backups resource collection.

Example

The example below returns an entity resource representation of a collection of parent and child backups created by Veeam Agent backup jobs. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=Backup&format=Entities&sortAsc=Name&filter=Platform==AgentForWindows    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
