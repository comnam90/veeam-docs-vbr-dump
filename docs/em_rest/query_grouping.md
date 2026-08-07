---
title: "Grouping Operators"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/query_grouping.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Grouping Operators


Within the filter component, you can group conditions by using the grouping operators “(“ and “)”. The grouping operators allow you to form complex queries that contain multiple logical expressions.

For example, using the query below, you can get a list of backup and replication jobs that meet the following criteria:

* Backup jobs with scheduling options enabled
* Replication jobs with scheduling options disabled

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=job&filter=(jobtype==replica;scheduleconfigured==false),(jobtype==backup;scheduleconfigured==true)  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Refs>     <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/795f2f57-6cc0-4c33-8c1b-bd7cd5df9aa7" Name="Fileserver Backup" UID="urn:veeam:Job:795f2f57-6cc0-4c33-8c1b-bd7cd5df9aa7">       <Links>         <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />         <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/795f2f57-6cc0-4c33-8c1b-bd7cd5df9aa7?format=Entity" Name="Fileserver Backup" />         <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/795f2f57-6cc0-4c33-8c1b-bd7cd5df9aa7/backupSessions" />       </Links>     </Ref>     <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/6c1375ec-e666-4b65-9537-d2d4b4b64dc8" Name="DC Replication" UID="urn:veeam:Job:6c1375ec-e666-4b65-9537-d2d4b4b64dc8">       <Links>         <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/15942270-fb56-4dcc-96e9-5f80e4725a15" Name="localhost" />         <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/6c1375ec-e666-4b65-9537-d2d4b4b64dc8?format=Entity" Name="DC Replication" />         <Link Rel="Down" Type="ReplicaJobSessionReferenceList" Href="https://localhost:9398/api/jobs/6c1375ec-e666-4b65-9537-d2d4b4b64dc8/replicaSessions" />       </Links>     </Ref>   </Refs>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=job&filter=(jobtype==replica;scheduleconfigured==true)%2c(jobtype==backup;name=="FileServer+Backup")&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=job&filter=(jobtype==replica;scheduleconfigured==true)%2c(jobtype==backup;name=="FileServer+Backup")&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

