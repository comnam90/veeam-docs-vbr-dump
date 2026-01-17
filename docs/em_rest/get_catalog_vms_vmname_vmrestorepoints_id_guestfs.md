---
title: "GET /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_catalog_vms_vmname_vmrestorepoints_id_guestfs.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of the hierarchy of the VM guest OS file system within a VM backup.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* Microsoft Hyper-V

Request

To get the hierarchy of the VM guest OS file system, send the GET HTTP request to the /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/ resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/ |

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

The response body contains links that let you browse the VM guest OS file system. Following the links, the client can get a list of all files and folders, a list of files only, a list of folders only as well as paginate display results.

Example

The example below returns a resource representation of the VM guest OS file system hierarchy for the exch01 VM:

|  |
| --- |
| Request:  GET https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <FileSystemEntry xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
