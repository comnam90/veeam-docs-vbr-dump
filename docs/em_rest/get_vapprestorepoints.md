---
title: "GET /vAppRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vapprestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /vAppRestorePoints


Returns a resource representation of a collection of vApp restore points created on backup servers that are connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of vApp restore points, send the [GET /query?type=vAppRestorePoint](get_query_vapprestorepoint.md) request. |

Supported Platforms

The request is supported for the VMware Cloud Director platform.

Request

To get a list of vApp restore points, send the GET HTTP request to the /vAppRestorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vAppRestorePoints |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
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

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /vAppRestorePoints resource collection.

Example

The example below returns a list of all vApp restore point created on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vAppRestorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/f139af13-0d49-49c1-bf88-8b2d0db621e3" Name="vApp2@2025-10-19 05:43:56" UID="urn:veeam:VAppRestorePoint:f139af13-0d49-49c1-bf88-8b2d0db621e3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/f3f9fa75-6984-451b-a8ca-f5a318161951" Name="Oct 19 2025  5:43AM" />       <Link Rel="Alternate" Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/f139af13-0d49-49c1-bf88-8b2d0db621e3?format=Entity" Name="vApp2@2025-10-19 05:43:56" />     </Links>   </Ref>   <Ref Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/8832a359-6af3-44de-9ae9-91feeee0d8c5" Name="vApp2@2025-10-19 06:07:11" UID="urn:veeam:VAppRestorePoint:8832a359-6af3-44de-9ae9-91feeee0d8c5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/5456cc77-bea7-48bc-9834-55bafd23760b" Name="Oct 19 2025  6:06AM" />       <Link Rel="Alternate" Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/8832a359-6af3-44de-9ae9-91feeee0d8c5?format=Entity" Name="vApp2@2025-10-19 06:07:11" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

