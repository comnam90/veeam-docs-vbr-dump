---
title: "GET /cloud/publicIpAddresses"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_publicipaddresses.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/publicIpAddresses


Returns a resource representation of a collection of public IP addresses. Public IP addresses are allocated in the service provider's network infrastructure and added to pools of public IP addresses on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of public IP addresses, send the [GET /query?type=CloudPublicIpAddress](get_query_cloudpublicipaddress.md) request. |

Request

To get a list of public IP addresses, send the GET HTTP request to the /cloud/publicIpAddresses resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses |

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

In the response body, the REST API returns a representation of the /cloud/publicIpAddresses resource collection.

Example

The example below returns a list of public IP addresses allocated in the service provider's network infrastructure and specified in Veeam Backup & Replication settings on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/publicIpAddresses  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/936db979-efbe-4ece-b279-07e24b4ea25e" Name="198.51.100.4" UID="urn:veeam:CloudPublicIpAddress:936db979-efbe-4ece-b279-07e24b4ea25e">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/936db979-efbe-4ece-b279-07e24b4ea25e?format=Entity" Name="198.51.100.4" />     </Links>   </Ref>   <Ref Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/11eebb50-5848-42a3-88cd-4932a5c8c894" Name="198.51.100.3" UID="urn:veeam:CloudPublicIpAddress:11eebb50-5848-42a3-88cd-4932a5c8c894">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/11eebb50-5848-42a3-88cd-4932a5c8c894?format=Entity" Name="198.51.100.3" />     </Links>   </Ref>   <Ref Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/fcf28ea0-6831-46ac-9abb-584e83a818ab" Name="198.51.100.9" UID="urn:veeam:CloudPublicIpAddress:fcf28ea0-6831-46ac-9abb-584e83a818ab">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/fcf28ea0-6831-46ac-9abb-584e83a818ab?format=Entity" Name="198.51.100.9" />     </Links>   </Ref>   <Ref Type="CloudPublicIpAddressReference" Href="https://localhost:9398/api/cloud/publicIpAddresses/45a2c7c1-232b-4a1d-814e-59db3b1329c4" Name="198.51.100.8" UID="urn:veeam:CloudPublicIpAddress:45a2c7c1-232b-4a1d-814e-59db3b1329c4">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/45a2c7c1-232b-4a1d-814e-59db3b1329c4?format=Entity" Name="198.51.100.8" />     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

