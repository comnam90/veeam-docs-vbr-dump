---
title: "Grouping Operators"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/query_grouping.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Grouping Operators


Within the filter component, you can group conditions by using the grouping operators “(“ and “)”. The grouping operators allow you to form complex queries that contain multiple logical expressions.

For example, using the query below, you can get a list of backup and replication jobs that meet the following criteria:

* Backup jobs with scheduling options enabled
* Replication jobs with scheduling options disabled

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=job&filter=(jobtype==replica;scheduleconfigured==false),(jobtype==backup;scheduleconfigured==true)    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


