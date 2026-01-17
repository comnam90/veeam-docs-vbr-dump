---
title: "GET /vCloud/orgConfigs/{ID}/backupJobSettings"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vcloud_orgconfigs_id_backupjobsettings.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns job settings applied to backup jobs for the VMware Cloud Director organization that has individual configuration with the specified ID.

Request

To get backup job settings used in the VMware Cloud Director organization configuration, send the GET HTTP request to the /vCloud/orgConfigs/{ID}/backupJobSettings resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID}/backupJobSettings |

Request Header

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

In the response body, the REST API returns a representation of the /vCloud/orgConfigs/{ID}/backupJobSettings resource.

Example

The example below returns a resource representation of the /vCloud/orgConfigs/{ID}/backupJobSettings resource.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7/backupJobSettings    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VCloudOrganizationConfigBackupJobSettings xmlns="http://www.veeam.com/ent/v1.0" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7/backupJobSettings"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
