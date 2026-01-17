---
title: "GET /catalog/vms/{vmname}/vmRestorePoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_catalog_vms_vmname_vmrestorepoints_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a VM restore point having the specified ID. The restore point is created for a VM having the specified name; guest OS files of the VM have been indexed during backup.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* Microsoft Hyper-V

Request

To get a VM restore point, send the GET HTTP request to the /catalog/vms/{vmname}/vmRestorePoints/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID} |

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

In the response body, the REST API returns a representation of the /catalog/vms/{vmname}/vmRestorePoints/{ID} resource.

Example

The example below returns a restore point having ID 7caf66d5-f700-442c-9aa9-8867f031377f for the srv04 VM:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CatalogVmRestorePointReference" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f" Name="10/19/2014 7:34:00 AM" UID="urn:veeam:CatalogVmRestorePoint:7caf66d5-f700-442c-9aa9-8867f031377f"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
