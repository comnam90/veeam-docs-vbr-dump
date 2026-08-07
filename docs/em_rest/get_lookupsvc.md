---
title: "GET /lookupSvc"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_lookupsvc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /lookupSvc


Returns a representation of the /lookupSvc resource. It contains a set of links of lookup queries that are composed for each hierarchy root — VMware and Hyper-V hosts added to backup servers that are managed by Veeam Backup Enterprise Manager. For detail, see [Virtual Infrastructure Lookup](lookup_service.md).

Request

To get a set of links of lookup queries, send the GET HTTP request to the /lookupSvc resource.

HTTP Request

|  |
| --- |
| GET https://localhost:9398/api/lookupSvc |

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

In the response body, the REST API returns a representation of the /lookupSvc resource.

Example

The sample request below returns set of links of lookup queries.

|  |
| --- |
| Request:  GET https://enterprise06.tech.local:9398/api/lookupSvc  Request Header:  X-RestSvcSessionId  NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <LookupSvc xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise06.tech.local:9398/api/lookupSvc" Type="LookupService" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise06.tech.local:9398/api/logonSessions/9c39e57f-00c8-4fec-ac65-856aad7db71f" Type="LogonSession" Rel="Up" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ade28dc43-b8ee-4e17-8e63-3d38b6604033&amp;name=\*&amp;type=Vm" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ade28dc43-b8ee-4e17-8e63-3d38b6604033&amp;name=\*&amp;type=Tag" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ade28dc43-b8ee-4e17-8e63-3d38b6604033&amp;name=\*&amp;type=StoragePod" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a83963a7e-d43f-4fea-9036-466898c9c9e7&amp;name=\*&amp;type=Vm" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a83963a7e-d43f-4fea-9036-466898c9c9e7&amp;name=\*&amp;type=Tag" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a83963a7e-d43f-4fea-9036-466898c9c9e7&amp;name=\*&amp;type=StoragePod" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a5d25f98b-90fb-452c-92a7-58e52adf2ed3&amp;name=\*&amp;type=Vm" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a5d25f98b-90fb-452c-92a7-58e52adf2ed3&amp;name=\*&amp;type=Organization" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a5d25f98b-90fb-452c-92a7-58e52adf2ed3&amp;name=\*&amp;type=OrgVdc" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a5d25f98b-90fb-452c-92a7-58e52adf2ed3&amp;name=\*&amp;type=Datastore" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a5d25f98b-90fb-452c-92a7-58e52adf2ed3&amp;name=\*&amp;type=OrgVdcStorageProfile" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a5d25f98b-90fb-452c-92a7-58e52adf2ed3&amp;name=\*&amp;type=Vapp" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a59016353-9017-489f-ae06-6f7e0a7ff286&amp;name=\*&amp;type=Vm" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a59016353-9017-489f-ae06-6f7e0a7ff286&amp;name=\*&amp;type=VmGroup" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a0bf40649-fd35-4184-ada4-777155a0a23c&amp;name=\*&amp;type=Vm" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a0bf40649-fd35-4184-ada4-777155a0a23c&amp;name=\*&amp;type=Tag" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a0bf40649-fd35-4184-ada4-777155a0a23c&amp;name=\*&amp;type=StoragePod" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ae77f37f4-4a47-4fc4-8261-7e8e8e0dd836&amp;name=\*&amp;type=Vm" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ae77f37f4-4a47-4fc4-8261-7e8e8e0dd836&amp;name=\*&amp;type=Organization" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ae77f37f4-4a47-4fc4-8261-7e8e8e0dd836&amp;name=\*&amp;type=OrgVdc" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ae77f37f4-4a47-4fc4-8261-7e8e8e0dd836&amp;name=\*&amp;type=Datastore" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ae77f37f4-4a47-4fc4-8261-7e8e8e0dd836&amp;name=\*&amp;type=OrgVdcStorageProfile" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3ae77f37f4-4a47-4fc4-8261-7e8e8e0dd836&amp;name=\*&amp;type=Vapp" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a4affbc8e-0dff-46bd-a409-881e41d2dcf5&amp;name=\*&amp;type=Vm" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a4affbc8e-0dff-46bd-a409-881e41d2dcf5&amp;name=\*&amp;type=Tag" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a4affbc8e-0dff-46bd-a409-881e41d2dcf5&amp;name=\*&amp;type=StoragePod" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a8b7885d9-a3ad-41f0-8cb0-a0646a5c75cc&amp;name=\*&amp;type=Vm" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a8b7885d9-a3ad-41f0-8cb0-a0646a5c75cc&amp;name=\*&amp;type=Tag" Type="HierarchyItemList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/lookup?host=urn%3aveeam%3aHierarchyRoot%3a8b7885d9-a3ad-41f0-8cb0-a0646a5c75cc&amp;name=\*&amp;type=StoragePod" Type="HierarchyItemList" Rel="Down" />     </Links> </LookupSvc> |

Page updated 2026-07-29

