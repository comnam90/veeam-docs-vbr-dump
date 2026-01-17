---
title: "GET /vmRestorePoints/{ID}/mounts/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vmrestorepoints_id_mountpoints_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a mount point having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a specific mount point, send the GET HTTP request to the /vmRestorePoints/{ID}/mounts/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vmRestorePoints/{ID}/mounts/{ID} |

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

In the response body, the REST API returns the /vmRestorePoints/{ID}/mounts/{ID} resource representation that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| FSRoots | DirectoryEntryListType | Collection of DirectoryEntry resources that represent VM guest OS files and folders in the VM file system hierarchy. For details, see [Directory Entries](#DirectoryEntries). |

Directory Entries

The DirectoryEntry resource contains the following parameters.

| Element | Type | Description |
| --- | --- | --- |
| Path | String | Path to the directory entry in the VM file system hierarchy, for example: C:\Shares. |
| Name | String | Name of the directory entry, for example: Shares. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /vmRestorePoints/{ID}/mounts/{ID} | Delete | URL for the [DELETE /vmRestorePoints/{ID}/mounts/{ID}](delete_vmrestorepoints_id_mountpoints_id.md) request. |

Example

The example below returns a resource representation of the mount point having ID 1 for the VM restore point having ID fb87163e-687d-4006-96c9-0451b5423b85:

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85/mounts/1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VmRestorePointMount xmlns="http://www.veeam.com/ent/v1.0" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85/mounts/1"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
