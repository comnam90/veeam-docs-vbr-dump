---
title: "GET /cloud/vlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vlans.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/vlans


Returns a resource representation of a collection of all virtual switches on which VLAN ranges for Veeam Cloud Connect Replication are reserved. VLANs are used for providing networking capabilities to tenant VM replicas. Virtual switches are configured on virtualization hosts that are used as a replication target and connected to backup servers managed by Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of VLANs, send the [GET /query?type=VlanConfiguration](get_query_vlanconfiguration.md) request. |

Request

To get a list of virtual switches with configured VLAN ranges, send the GET HTTP request to the /cloud/vlans resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/vlans |

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

In the response body, the REST API returns a representation of the /cloud/vlans resource collection.

Example

The example below returns a list of virtual switches with configured VLAN ranges. Virtual switches are configured on virtualization hosts that are used as a replication target and connected to backup servers managed by Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/vlans  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533" Name="vSwitch0" UID="urn:veeam:VlanConfiguration:78c6a038-38a2-4908-ac19-1540f9448533">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="VlanConfiguration" Href="https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533?format=Entity" Name="vSwitch0" />     </Links>   </Ref>   <Ref Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/510f34ea-1534-437c-a746-f32cf0f712aa" Name="Intel(R) I350 Gigabit Network Connection - Virtual Switch" UID="urn:veeam:VlanConfiguration:510f34ea-1534-437c-a746-f32cf0f712aa">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="VlanConfiguration" Href="https://localhost:9398/api/cloud/vlans/510f34ea-1534-437c-a746-f32cf0f712aa?format=Entity" Name="Intel(R) I350 Gigabit Network Connection - Virtual Switch" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

