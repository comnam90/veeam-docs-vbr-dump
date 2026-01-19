---
title: "GET /nas/jobs/{ID}/includes/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_jobs_id_includes_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /nas/jobs/{ID}/includes/{ID}


Returns a representation of a file or folder having the specified ID and processed by the file share backup job having the specified ID.

Request

To get a representation of a file or folder processed by the file share backup job, send the GET HTTP request to the /nas/jobs/{ID}/includes/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/jobs/{ID}/includes/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /nas/jobs/includes/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| HierarchyObjRef | HierarchyObjRefType | Reference to file or folder processed by the file share backup job, for example: urn:NasBackup:FileServer:ee50f2fb-034f-41cd-8dc8-904aeae2d0d8. |
| ObjectInJobId | String | ID of the file or folder processed by the file share backup job, for example: e310aa12-eff2-41f4-97c8-631b677fc17f. |
| FileOrFolder | String | Path to the file or folder processed by the job, for example: C:\File Share. |
| FileServerUid | UidType | UID of the file share resource related to this file or folder, for example: urn:veeam:FileServer:f5d9ea1f-ef70-4e51-af3d-c760380d5347. |
| InclusionMask | FileExtensionInfoListType | File extensions for files included in the job processing. Represents a list of string Extension parameters. |
| ExclusionMask | FileExtensionInfoListType | File extensions for files excluded from the job processing. Represents a list of string Extension parameters. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=NasObject](get_query_nasobject.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /nas/jobs/{ID} | Up | URL of the [/nas/jobs/{ID}](nas_jobs_id.md) resource — a file share backup job that backs up the file share. |
| /nas/fileservers/{ID} | Related | URL of the [/nas/fileServers/{ID}](nas_fileservers_id.md) resource related to this [/nas/jobs/{ID}/includes/{ID}](nas_jobs_id_includes_id.md) resource. |

Example

A sample request below returns a resource representation of the VM having ID 83071dc0-44f2-49b6-b431-1cb79ed66639 that is processed by the job having ID da4a15c2-04e7-4135-b876-577249d3d720.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/jobs/da4a15c2-04e7-4135-b876-577249d3d720/includes/83071dc0-44f2-49b6-b431-1cb79ed66639    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <NASObject xmlns="http://www.veeam.com/ent/v1.0" Type="NasObject" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/includes/6fefb504-856d-4c31-b767-76af5567c407"> |


