---
title: "GET /backupFiles/{ID}/vmRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupfiles_id_vmrestorepoints.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a collection of restore points for separate VMs in a backup file with the specified ID. The backup file was created on or imported to the backup server connected to Veeam Backup Enterprise Manager.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a collection of restore points for separate VMs in a backup file, send the GET HTTP request to the /backupFiles/{ID}/vmRestorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupFiles/{ID}/vmRestorePoints |

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

In the response body, the REST API returns a representation of the /backupFiles/{ID}/vmRestorePoints resource.

Example

The example below returns a collection of restore points for separate VMs in a backup file with ID 98c2ba69-16b8-4162-80a4-c6ba1a2ff02c.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupFiles/98c2ba69-16b8-4162-80a4-c6ba1a2ff02c/vmRestorePoints    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
