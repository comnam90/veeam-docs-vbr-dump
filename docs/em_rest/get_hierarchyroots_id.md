---
title: "GET /hierarchyRoots/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_hierarchyroots_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /hierarchyRoots/{ID}


Returns a resource representation of a virtualization host having the specified ID. The virtualization host is added to the backup server connected to Veeam Backup Enterprise Manager.

Request

To get a virtualization host, send the GET HTTP request to the /hierarchyRoots/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/hierarchyRoots/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /hierarchyRoots/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the hierarchy root resource, for example: urn:veeam:HierarchyRoot:195c7259-8d89-4f6e-9098-25ee1f432669. |
| Name | String | Name of the hierarchy root resource, for example: 172.16.12.21. |
| HierarchyRootId | String | ID of the hierarchy root resource, for example: 195c7259-8d89-4f6e-9098-25ee1f432669. |
| UniqueId | String | Unique ID of the hierarchy root, or virtualization host (for example, vCenter InstanceUUID or DNS name of the Hyper-V host). |
| HostType | String | Type of the virtualization host. Possible values:   * ESX * VC * ESXi * HvServer * HvCluster * Scvmm * VcdSystem |

To view query parameters that you can use for filtering or sorting, see  [GET /query?type=HierarchyRoot](get_query_hierarchyroot.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that contains the hierarchy root in the backup infrastructure. |
| /hierarchyRoots/{ID} | Alternate | Alternate URL of the [/hierarchyRoots/{ID}](hierarchyroots_id.md) resource. |
| /managedServers/{ID} | Related | URL of the [/managedServers/{ID}](managedservers_id.md) resource — a managed server resource related to the hierarchy root. |

Example

The example below returns an entity representation of a virtualization host having ID d68c782f-ec0a-4bf3-b3c1-04c552b64fdf:

|  |
| --- |
| Request:  GET https://localhost:9398/api/hierarchyRoots/d68c782f-ec0a-4bf3-b3c1-04c552b64fdf?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |


