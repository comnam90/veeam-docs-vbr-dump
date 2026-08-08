---
title: "GET /reports/summary/vms\_overview"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_reports_summary_vms_overview.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /reports/summary/vms\_overview


Returns a resource representation of an overview report about backed up and replicated VMs, available restore points and so on.

Request

To get a VM overview report, send the GET HTTP request to the /reports/summary/vms\_overview resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/reports/summary/vms\_overview |

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

In the response body, the REST API returns a representation of the /reports/summary/vms\_overview resource.

Example

The example below returns a VM overview report informing about backed up and replicated VMs, available restore points and so on.

|  |
| --- |
| Request:  GET https://localhost:9398/api/reports/summary/vms\_overview  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <VmsOverviewReportFrame xmlns="http://www.veeam.com/ent/v1.0">   <ProtectedVms>6</ProtectedVms>   <BackedUpVms>5</BackedUpVms>   <ReplicatedVms>2</ReplicatedVms>   <RestorePoints>11</RestorePoints>   <FullBackupPointsSize>0</FullBackupPointsSize>   <IncrementalBackupPointsSize>0</IncrementalBackupPointsSize>   <ReplicaRestorePointsSize>0</ReplicaRestorePointsSize>   <SourceVmsSize>70944288914</SourceVmsSize>   <SuccessBackupPercents>100</SuccessBackupPercents>   <ProtectedVmsReportLink>Workspace/ViewReport.aspx?definition=8a56d84f-1790-4f54-ab20-2e0bfdefa16b&amp;ShowParams=1</ProtectedVmsReportLink> </VmsOverviewReportFrame> |

Page updated 2026-07-29

