---
title: "GET /query?type=HierarchyRoot"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_hierarchyroot.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=HierarchyRoot


Returns a resource representation of a collection of virtualization hosts added to backup servers connected to Veeam Backup Enterprise Manager. For details, see [/hierarchyRoots](hierarchyroots.md).

Request

To get a list of virtualization hosts, send the GET HTTP request to the query with the type parameter set to HierarchyRoot.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=HierarchyRoot |

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
| UID | UidType | UID of the hierarchy root resource, for example: urn:veeam:HierarchyRoot:195c7259-8d89-4f6e-9098-25ee1f432669. |
| Name | String | Name of the hierarchy root resource, for example: 172.16.12.21. |
| UniqueId | String | Unique ID of the hierarchy root, or virtualization host (for example, vCenter InstanceUUID or DNS name of the Hyper-V host). |
| HostType | String | Type of the virtualisation host. Possible values:   * ESX * VC * ESXi * HvServer * HvCluster * Scvmm * VcdSystem |
| BackupServerUid | UidType | UID of the backup server to which the hierarchy root, or virtualization host, is added. |
| BackupServerName | String | Name of the backup server to which the hierarchy root, or virtualization host, is added. |

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

In the response body, the REST API returns a representation of the /hierarchyRoots resource collection.

Example

The example below returns an entity resource representation of a collection of VMware vCenter Servers managed the backup server with name enterprise06.tech.local. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=HierarchyRoot&format=Entities&sortAsc=Name&filter=HostType==VC;BackupServerName=="enterprise06.tech.local"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <HierarchyRoots>       <HierarchyRoot Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/8b7885d9-a3ad-41f0-8cb0-a0646a5c75cc?format=Entity" Name="vcenter03.tech.local" UID="urn:veeam:HierarchyRoot:8b7885d9-a3ad-41f0-8cb0-a0646a5c75cc">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/8b7885d9-a3ad-41f0-8cb0-a0646a5c75cc" Name="vcenter03.tech.local" />           <Link Rel="Related" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/8b7885d9-a3ad-41f0-8cb0-a0646a5c75cc?format=Entity" Name="vcenter03.tech.local" />         </Links>         <HierarchyRootId>8b7885d9-a3ad-41f0-8cb0-a0646a5c75cc</HierarchyRootId>         <UniqueId>d766a026-a7a7-4d6e-add0-9599a291394f</UniqueId>         <HostType>VC</HostType>       </HierarchyRoot>       <HierarchyRoot Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/de28dc43-b8ee-4e17-8e63-3d38b6604033?format=Entity" Name="vcenter01.tech.local" UID="urn:veeam:HierarchyRoot:de28dc43-b8ee-4e17-8e63-3d38b6604033">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/de28dc43-b8ee-4e17-8e63-3d38b6604033" Name="vcenter01.tech.local" />           <Link Rel="Related" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/de28dc43-b8ee-4e17-8e63-3d38b6604033?format=Entity" Name="vcenter01.tech.local" />         </Links>         <HierarchyRootId>de28dc43-b8ee-4e17-8e63-3d38b6604033</HierarchyRootId>         <UniqueId>13660d26-9451-41ea-88f4-ca4aca217dff</UniqueId>         <HostType>VC</HostType>       </HierarchyRoot>       <HierarchyRoot Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/4affbc8e-0dff-46bd-a409-881e41d2dcf5?format=Entity" Name="vcentercdp-virt.tech.local" UID="urn:veeam:HierarchyRoot:4affbc8e-0dff-46bd-a409-881e41d2dcf5">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/4affbc8e-0dff-46bd-a409-881e41d2dcf5" Name="vcentercdp-virt.tech.local" />           <Link Rel="Related" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/4affbc8e-0dff-46bd-a409-881e41d2dcf5?format=Entity" Name="vcentercdp-virt.tech.local" />         </Links>         <HierarchyRootId>4affbc8e-0dff-46bd-a409-881e41d2dcf5</HierarchyRootId>         <UniqueId>b34e780b-3cf1-4504-b0bd-e39d0eaef2ff</UniqueId>         <HostType>VC</HostType>       </HierarchyRoot>     </HierarchyRoots>   </Entities> |

Page updated 2026-07-29

