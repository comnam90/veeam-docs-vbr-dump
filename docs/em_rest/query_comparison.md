---
title: "Comparison Expressions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/query_comparison.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Comparison Expressions


Comparison expressions let you compare resource parameters with specific values. Comparison expressions have the following format:

|  |
| --- |
| <parameter><operator><value> |

where:

* <parameter> is a name of the query parameter that you are able to use for filtering.

To learn what query parameters are available for a specific resource, see the Query Parameters section in the GET HTTP method description of the resource. For example, [GET /backupServers/{ID}](get_backupservers_id.md).

* <operator> is an operator that compares the parameter and value. For details, see [Comparison Operators](#operators).
* <value> is a parameter value.

Comparison Operators

Comparison expression may contain the following operators.

Comparison Operators

| Comparison Operator | Query Syntax Character | Description |
| Greater | > | The resource parameter must be greater than the specified value. |
| Less | < | The resource parameter must be less than the specified value. |
| Equal | == | The resource parameter must be equal to the specified value. |
| Does not equal | != | The resource parameter must not be equal to the specified value. |
| Greater or equal | >= | The resource parameter must be greater than or equal to the specified value. |
| Less or equal | <= | The resource parameter must be less than or equal to the specified value. |

|  |
| --- |
| Note |
| If a resource parameter has an array of possible values, the values are compared by their index. For example, the Result parameter of a backup job session has the following possible values listed in the acceding order:   * Success * Warning * Failed   In this example, the Failed value is greater than the Success value. |

Example

To get a backup job with the Exchange Backup name, use the following query.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=job&filter=name=="Exchange Backup"  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Refs>     <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5" Name="Exchange Backup" UID="urn:veeam:Job:568c42ce-eb11-4140-92cf-39ab36712bf5">       <Links>         <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/21a631e0-af7f-46ba-afbd-273de2e6fd4a" Name="localhost" />         <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?format=Entity" Name="Exchange Backup" />         <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5/backupSessions" />       </Links>     </Ref>   </Refs>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=job&filter=(name=="Exchange+Backup")&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=job&filter=(name=="Exchange+Backup")&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

