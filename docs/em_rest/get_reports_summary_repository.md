---
title: "GET /reports/summary/repository"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_reports_summary_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /reports/summary/repository


Returns an overview report about backup repositories, their capacity, free space and size of backup files on these backup repositories.

Request

To get a repositories report, send the GET HTTP request to the /reports/summary/repository resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/reports/summary/repository |

Request Header

The request contains the following headers:

Request Header

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

In the response body, the REST API returns a representation of the /reports/summary/repository resource.

Example

The example below returns a statistics report informing about backup repositories, their capacity, free space and size of backup files on these backup repositories.

|  |
| --- |
| Request:  GET https://localhost:9398/api/reports/summary/repository  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <RepositoryReportFrame xmlns="http://www.veeam.com/ent/v1.0" CapacityPlanningReportLink="Workspace/ViewReport.aspx?definition=62221565-102c-4ec8-851b-d61c03d972d1&amp;ShowParams=1">   <Period>     <Name>Omega Cloud Vol2</Name>     <Capacity>322122547200</Capacity>     <FreeSpace>321163100160</FreeSpace>     <BackupSize>959447040</BackupSize>   </Period>   <Period>     <Name>NetApp SnapShot</Name>     <Capacity>-1</Capacity>     <FreeSpace>-1</FreeSpace>     <BackupSize>0</BackupSize>   </Period>   <Period>     <Name>Alpha Repository</Name>     <Capacity>10737418240</Capacity>     <FreeSpace>10737418240</FreeSpace>     <BackupSize>0</BackupSize>   </Period>   <Period>     <Name>Backup Volume 01</Name>     <Capacity>1079639011328</Capacity>     <FreeSpace>881812750336</FreeSpace>     <BackupSize>197826260992</BackupSize>   </Period>   <Period>     <Name>Default Backup Repository</Name>     <Capacity>128479916032</Capacity>     <FreeSpace>105921257472</FreeSpace>     <BackupSize>22558658560</BackupSize>   </Period>   <Period>     <Name>Omega Cloud Vol1</Name>     <Capacity>536870912000</Capacity>     <FreeSpace>527646588928</FreeSpace>     <BackupSize>9224323072</BackupSize>   </Period> </RepositoryReportFrame> |

Page updated 2026-07-29

