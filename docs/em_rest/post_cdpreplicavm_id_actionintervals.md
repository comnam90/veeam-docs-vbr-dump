---
title: "POST /cdpReplicas/{ID}/vms/{ID}?action=intervals"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_cdpreplicavm_id_actionintervals.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# POST /cdpReplicas/{ID}/vms/{ID}?action=intervals


Returns a collection of available intervals for the specified VM included in the specified CDP replica.

Request

To get a collection of available intervals for the specified VM, send the POST HTTP request to the /cdpReplicas/{ID}/vms/{ID}?action=intervals URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cdpReplicas/{ID}/vms/{ID}?action=intervals |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

The request body must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| StartDate | DateTime | The earliest start date and time for the returning intervals. The parameter accepts only UTC-formatted DateTime values. | Yes | 1/1 |
| EndDate | DateTime | The latest end date and time for the returning intervals. The parameter accepts only UTC-formatted DateTime values. | Yes | 1/1 |

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

In the response body, the REST API returns a representation of the /cdpReplicaIntervals resource.

Example

The example below returns a collection of available intervals for the VM that has ID e809a086-2562-4a0f-a9a8-9c115ff8f0ba and that is included in the CDP replica with ID 7665222c-2e99-4a3f-b892-1827ba8d1eee.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee/vms/e809a086-2562-4a0f-a9a8-9c115ff8f0ba?action=intervals    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Request Body:  <?xml version="1.0" encoding="utf-8"?>    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> <CdpReplicaIntervals xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <StartDate>2023-02-16T16:57:44</StartDate>   <EndDate>2023-02-17T16:57:44</EndDate>   <HasApplicationConsistentState>true</HasApplicationConsistentState>   <Intervals>     <Interval>       <StartDate>2023-02-17T07:01:25</StartDate>       <EndDate>2023-02-17T07:01:30</EndDate>       <Rpo>5</Rpo>       <IntervalType>RestoreAvailable</IntervalType>     </Interval>     <Interval>       <StartDate>2023-02-17T07:01:30</StartDate>       <EndDate>2023-02-17T16:56:15</EndDate>       <Rpo>15</Rpo>       <IntervalType>RestoreAvailable</IntervalType>     </Interval>     <Interval>       <StartDate>2023-02-17T16:56:15</StartDate>       <EndDate>2023-02-17T16:56:22</EndDate>       <Rpo>7</Rpo>       <IntervalType>RestoreAvailable</IntervalType>     </Interval>   </Intervals>   <RestorePoints>     <RestorePoint>       <Id>56eec589-6e13-47d8-ac3a-6d9c2821179c</Id>       <Date>2023-02-16T23:00:49</Date>       <IsApplicationConsistent>true</IsApplicationConsistent>     </RestorePoint>     <RestorePoint>       <Id>1862add3-41dd-4a39-ba1e-15c766c4b0a5</Id>       <Date>2023-02-17T07:01:21</Date>       <IsApplicationConsistent>true</IsApplicationConsistent>     </RestorePoint>     <RestorePoint>       <Id>754dfdf5-680f-4e4e-9234-e5d57e339173</Id>       <Date>2023-02-17T15:00:47</Date>       <IsApplicationConsistent>true</IsApplicationConsistent>     </RestorePoint>   </RestorePoints> </CdpReplicaIntervals> |


