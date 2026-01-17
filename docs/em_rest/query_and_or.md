---
title: "Logical Operators: AND, OR"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/query_and_or.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Logical Operators: AND, OR


The filter component in the query string may contain any number of comparison expressions. You can unite multiple comparison expressions with AND and OR logical operators.

| Logical Operator | Query Syntax Character | Description |
| --- | --- | --- |
| AND | ; (Semicolon) | All conditions specified in the filter parameter must be true. |
| OR | , (Comma) | Any of the conditions specified in the filter parameter must be true |

For example, using the query below, you can get a list of jobs of the Backup type that are created for VMs on the Hyper-V platform:

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=job&filter=jobtype==backup;platform==hyperv    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


