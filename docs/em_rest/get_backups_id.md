---
title: "GET /backups/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backups_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a backup having the specified ID. The backup is created on or imported to the backup server connected to Veeam Backup Enterprise Manager.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a backup, send the GET HTTP request to the /backups/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backups/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /backups/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the backup resource, for example: urn:veeam:Backup:58c917c7-7b7a-41ff-8676-226656c35c05. |
| Name | String | Name of the backup job parent to the backup, for example: SQL Backup. |
| Platform | String | Type of a platform of a backup resource. Possible values:   * VMware — for protected VMware vSphere VMs. * HyperV — for protected Microsoft Hyper-V VMs. * vCloud — for protected VMware Cloud Director resources. * AgentForLinux — for machines protected with Veeam Agent for Linux. * AgentForWindows — for machines protected with Veeam Agent for Windows. * CustomPlatform — for Nutanix and other custom platforms. |
| BackupType | String | Type of a backup resource. Possible values:   * Standard — for VMware, HyperV, vCloud and Standalone Veeam Backup Agent backup resources. * ParentBackup — for backup container resources. Represents a backup created by a Veeam Agent backup job in the Veeam Agent Management scenario, and contains links for child backups. * ChildBackup — for backup resources that have links to restore points and parent backups. Represents a backup of a separate machine in the backup created by a Veeam Agent backup job in the Veeam Agent Management scenario. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=Backup](get_query_backup.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /repositories/{ID} | Up | URL of the [/repositories/{ID}](repositories_id.md) resource — a repository where the backup is stored. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource parent to the backup. |
| /backups/{ID} | Alternate | Alternate URL of the [/backups/{ID}](backups_id.md) resource. |
| /backups/{ID}/restorePoints | Down | URL of the [/restorePoints](restorepoints.md) resource — a collection of restore points contained in the backup. |
| /backups/{ID}/backupFiles | Down | URL of the [/backupFiles](backupfiles.md) resource — a collection of backup files contained in the backup. |

Example

The example below returns an entity resource representation of a backup having ID 2e734096-56ea-4f36-ac2a-15546518d26c:

|  |
| --- |
| Request:  GET https://enterprise04.tech.local:9398/api/backups/2e734096-56ea-4f36-ac2a-15546518d26c?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
