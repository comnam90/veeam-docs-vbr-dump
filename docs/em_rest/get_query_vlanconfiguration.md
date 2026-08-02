---
title: "GET /query?type=VlanConfiguration"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vlanconfiguration.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=VlanConfiguration


Returns a resource representation of a collection of all virtual switches on which VLAN ranges for Veeam Cloud Connect Replication are reserved. For details, see [/cloud/vlans](vlans.md).

Request

To get a list of virtual switches with configured VLAN ranges, send the GET HTTP request to the query with the type parameter set to VlanConfiguration.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=VlanConfiguration |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | String | ID of the virtual switch in the Veeam infrastructure, for example: 510f34ea-1534-437c-a746-f32cf0f712aa. |
| SwitchName | String | Name of the virtual switch, for example: Intel(R) I350 Gigabit Network Connection - Virtual Switch. |
| SwitchType | String | Type of the virtual switch. Possible values:   * VirtualSwitch * DistributedVirtualSwitch |
| SwitchId | String | ID of the virtual switch in the virtualization infrastructure, for example: 4670EE6D-66BE-4A1C-A58E-6389CA99BD3E. |
| ClusterName | String | Name of the host or cluster on which the virtual switch with VLAN ranges is configured. |
| ClusterRef | HierarchyObjRefType | Reference to the host or cluster on which the virtual switch with VLAN ranges is configured, for example: urn:VMware:Host:4a3f28d9-d4f3-4e4c-9afb-91db8ab57436.host-438. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. |
| BackupServerUid | UidType | UID of the backup server parent to the VLAN configuration resource. |
| BackupServerName | String | Name of the backup server parent to the VLAN configuration resource. |

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

In the response body, the REST API returns a representation of the //cloud/vlans resource collection.

Example

The example below returns an entity resource representation of a collection of virtual switches that were added on the backup server that has ID ca19249e-e638-421a-ab22-68cb89b9009a. The results are ordered in the acceding order by the SwitchName parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VlanConfiguration&format=Entities&sortAsc=SwitchName&filter=BackupServerUid=="ca19249e-e638-421a-ab22-68cb89b9009a"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <VlanConfigurations>       <Vlans Name="Intel(R) I350 Gigabit Network Connection - Virtual Switch" UID="eddf9f5b-4dbc-4222-8014-fec97352c74c">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/eddf9f5b-4dbc-4222-8014-fec97352c74c" Name="Intel(R) I350 Gigabit Network Connection - Virtual Switch" />           <Link Rel="Edit" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/eddf9f5b-4dbc-4222-8014-fec97352c74c" Name="Intel(R) I350 Gigabit Network Connection - Virtual Switch" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/vlans/eddf9f5b-4dbc-4222-8014-fec97352c74c" />         </Links>         <HostRef>urn:HyperV:Vm:423d0b64-96ba-4553-a8ce-03906fbce48b.</HostRef>         <PlatformType>HyperV</PlatformType>         <VlanIdsWithInternetLeftBound>701</VlanIdsWithInternetLeftBound>         <VlanIdsWithInternetRightBound>705</VlanIdsWithInternetRightBound>         <VlanIdsWithoutInternetLeftBound>706</VlanIdsWithoutInternetLeftBound>         <VlanIdsWithoutInternetRightBound>710</VlanIdsWithoutInternetRightBound>         <SwitchName>Intel(R) I350 Gigabit Network Connection - Virtual Switch</SwitchName>         <SwitchId>4670EE6D-66BE-4A1C-A58E-6389CA99BD3E</SwitchId>         <SwitchType>VirtualSwitch</SwitchType>       </Vlans>       <Vlans Name="vSwitch0" UID="ba266d50-2f00-4acc-b864-06d07ea7afd0">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/ba266d50-2f00-4acc-b864-06d07ea7afd0" Name="vSwitch0" />           <Link Rel="Edit" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/ba266d50-2f00-4acc-b864-06d07ea7afd0" Name="vSwitch0" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/vlans/ba266d50-2f00-4acc-b864-06d07ea7afd0" />         </Links>         <HostRef>urn:VMware:Host:4891af87-a201-4a50-bf3f-372ca2441ab0.host-78094</HostRef>         <PlatformType>VMware</PlatformType>         <VlanIdsWithInternetLeftBound>721</VlanIdsWithInternetLeftBound>         <VlanIdsWithInternetRightBound>725</VlanIdsWithInternetRightBound>         <VlanIdsWithoutInternetLeftBound>726</VlanIdsWithoutInternetLeftBound>         <VlanIdsWithoutInternetRightBound>730</VlanIdsWithoutInternetRightBound>         <SwitchName>vSwitch0</SwitchName>         <SwitchId>vSwitch0</SwitchId>         <SwitchType>VirtualSwitch</SwitchType>       </Vlans>       <Vlans Name="vSwitch0" UID="66471e62-35ed-4742-b045-8a372fd77aa8">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/66471e62-35ed-4742-b045-8a372fd77aa8" Name="vSwitch0" />           <Link Rel="Edit" Type="VlanConfigurationReference" Href="https://localhost:9398/api/cloud/vlans/66471e62-35ed-4742-b045-8a372fd77aa8" Name="vSwitch0" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/vlans/66471e62-35ed-4742-b045-8a372fd77aa8" />         </Links>         <HostRef>urn:VMware:Host:78b52627-bda9-46d9-92fe-5093287c771c.host-42428</HostRef>         <PlatformType>VMware</PlatformType>         <VlanIdsWithInternetLeftBound>711</VlanIdsWithInternetLeftBound>         <VlanIdsWithInternetRightBound>715</VlanIdsWithInternetRightBound>         <VlanIdsWithoutInternetLeftBound>716</VlanIdsWithoutInternetLeftBound>         <VlanIdsWithoutInternetRightBound>720</VlanIdsWithoutInternetRightBound>         <SwitchName>vSwitch0</SwitchName>         <SwitchId>vSwitch0</SwitchId>         <SwitchType>VirtualSwitch</SwitchType>       </Vlans>     </VlanConfigurations>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=VlanConfiguration&format=Entities&sortAsc=SwitchName&filter=BackupServerUid=="ca19249e-e638-421a-ab22-68cb89b9009a"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=VlanConfiguration&format=Entities&sortAsc=SwitchName&filter=BackupServerUid=="ca19249e-e638-421a-ab22-68cb89b9009a"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

