---
title: "sortAsc, sortDesc"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/sortasc_sortdesc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# sortAsc, sortDesc


The sortAsc and sortDesc query parameters let you sort the displayed items in the ascending or descending order. The displayed items are sorted by a specific field that is passed to the query as an argument.

For example, using the query below, you can get a list of backup servers connected to Veeam Backup Enterprise Manager sorted by the ‘Name’ field in the descending order:

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=backupServer&sortDesc=name  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Refs>     <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" UID="urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982">       <Links>         <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982/jobs" />         <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982/repositories" />         <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982/credentials" />         <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982/passwords" />         <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982?format=Entity" Name="172.17.53.48" />         <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982/managedServers" />       </Links>     </Ref>     <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb" Name="172.17.53.47" UID="urn:veeam:BackupServer:e42211aa-321d-4f91-9c13-2342cf9557eb">       <Links>         <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/jobs" />         <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/repositories" />         <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/credentials" />         <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/passwords" />         <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb?format=Entity" Name="172.17.53.47" />         <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/managedServers" />       </Links>     </Ref>   </Refs>   <PagingInfo PageNum="1" PageSize="100" PagesCount="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=backupServer&sortDesc=name&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=backupServer&sortDesc=name&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

