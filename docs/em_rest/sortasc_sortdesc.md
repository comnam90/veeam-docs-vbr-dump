---
title: "sortAsc, sortDesc"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/sortasc_sortdesc.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The sortAsc and sortDesc query parameters let you sort the displayed items in the ascending or descending order. The displayed items are sorted by a specific field that is passed to the query as an argument.

For example, using the query below, you can get a list of backup servers connected to Veeam Backup Enterprise Manager sorted by the ‘Name’ field in the descending order:

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=backupServer&sortDesc=name    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
