---
title: "pageSize, page"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/pagesize_and_page.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# pageSize, page


The pageSize and page query parameters let you control pagination.

pageSize

Using the pageSize parameter, you can define the number of items to be displayed on one page. As a result, the server will return a set of pages with the defined number of items per page.

By default, all query results are displayed on one page. To set the pageSize parameter, you should pass a value greater than 0 as a query argument.

For example, using the query below, you can paginate a list of backup serves, 1 backup server per page:

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=backupServer&pageSize=1  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Refs>     <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb" Name="172.17.53.47" UID="urn:veeam:BackupServer:e42211aa-321d-4f91-9c13-2342cf9557eb">       <Links>         <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/jobs" />         <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/repositories" />         <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/credentials" />         <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/passwords" />         <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb?format=Entity" Name="172.17.53.47" />         <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/e42211aa-321d-4f91-9c13-2342cf9557eb/managedServers" />       </Links>     </Ref>   </Refs>   <PagingInfo PageNum="1" PageSize="1" PagesCount="2">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=backupServer&pageSize=1&page=1" />       <Link Rel="Next" Href="https://localhost:9398/api/query?type=backupServer&pageSize=1&page=2" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=backupServer&pageSize=1&page=2" />     </Links>   </PagingInfo> </QueryResult> |

page

In the PagingInfo section of the returned resource representation, Veeam Backup Enterprise Manager returns URLs to pages with results. The page parameter in the URL defines the number of displayed page.

For example, the page=2 string in the URL below defines that the displayed page is the second page with query results:

|  |
| --- |
| https://localhost:9398/api/query?type=BackupServer&pageSize=1&page=2 |

|  |
| --- |
| Tip |
| You can move forward or backward the pages with query results by following the links in PagingInfo section in the query results. Alternatively, you can manually increase or decrease the page number in the query string. |

Page updated 2026-07-29

