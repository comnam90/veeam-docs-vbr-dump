---
title: "Logical Operators: AND, OR"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/query_and_or.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Logical Operators: AND, OR


The filter component in the query string may contain any number of comparison expressions. You can unite multiple comparison expressions with AND and OR logical operators.

Logical Operators: AND, OR

| Logical Operator | Query Syntax Character | Description |
| AND | ; (Semicolon) | All conditions specified in the filter parameter must be true. |
| OR | , (Comma) | Any of the conditions specified in the filter parameter must be true |

For example, using the query below, you can get a list of jobs of the Backup type that are created for VMs on the Hyper-V platform:

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=job&filter=jobtype==backup;platform==hyperv  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Refs>     <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/de14a4c9-3fb9-419b-b622-c6e3ebda28cb" Name="Exchange Backup" UID="urn:veeam:Job:de14a4c9-3fb9-419b-b622-c6e3ebda28cb">       <Links>         <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />         <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/de14a4c9-3fb9-419b-b622-c6e3ebda28cb?format=Entity" Name="Exchange Backup" />         <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/de14a4c9-3fb9-419b-b622-c6e3ebda28cb/backupSessions" />       </Links>     </Ref>     <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/dce85686-59c8-42c4-8766-f1c00a5b8067" Name="SQL" UID="urn:veeam:Job:dce85686-59c8-42c4-8766-f1c00a5b8067">       <Links>         <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />         <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/dce85686-59c8-42c4-8766-f1c00a5b8067?format=Entity" Name="SQL" />         <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/dce85686-59c8-42c4-8766-f1c00a5b8067/backupSessions" />       </Links>     </Ref>   </Refs>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=job&filter=jobtype==backup;platform==hyperv&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=job&filter=jobtype==backup;platform==hyperv&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

