---
title: "GET /jobs/{ID}/includes/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_jobs_id_includes_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /jobs/{ID}/includes/{ID}


Returns a representation of a VM or a VM container having the specified ID and processed by the job having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a representation of a VM or a VM container processed by the job, send the GET HTTP request to the /jobs/{ID}/includes/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/jobs/{ID}/includes/{ID} |

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

In the response body, the REST API returns the /jobs/{ID}/includes/{ID} resource that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| ObjectInJobId | String | ID of the VM or VM container processed by the job, for example: e310aa12-eff2-41f4-97c8-631b677fc17f. |
| HierarchyObjRef | HierarchyObjRefType | Reference to the VM or VM container added to the job, for example: urn:VMware:Vm:d68c782f-ec0a-4bf3-b3c1-04c552b64fdf.vm-85541. |
| Name | String | Name of the VM or VM container processed by the job, for example: DC-SRV. |
| DisplayName | String | Display name of the VM or VM container processed by the job, for example: DC-SRV. |
| GuestProcessingOptions | GuestProcessingOptionsType | Options for application-aware image processing. For details, see [Guest Processing Options](guestprocessingoptions.md). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=ObjectInJob](get_query_objectinjob.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /jobs/{ID} | Up | URL of the [/jobs/{ID}](jobs_id.md) resource — a job that processes the object. |
| /jobs/{ID}/includes/{ID} | Delete | URL for the [DELETE /jobs/{ID}/includes/{ID}](delete_jobs_id_includes_id.md) request. |

Example

A sample request below returns a resource representation of the VM having ID 83071dc0-44f2-49b6-b431-1cb79ed66639 that is processed by the job having ID da4a15c2-04e7-4135-b876-577249d3d720.

|  |
| --- |
| Request:  GET https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720/includes/83071dc0-44f2-49b6-b431-1cb79ed66639    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <ObjectInJob xmlns="http://www.veeam.com/ent/v1.0" Type="ObjectInJob" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720/includes/83071dc0-44f2-49b6-b431-1cb79ed66639"> |


