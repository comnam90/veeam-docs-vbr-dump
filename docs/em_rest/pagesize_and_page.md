---
title: "pagesize_and_page"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/pagesize_and_page.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The pageSize and page query parameters let you control pagination.

pageSize

Using the pageSize parameter, you can define the number of items to be displayed on one page. As a result, the server will return a set of pages with the defined number of items per page.

By default, all query results are displayed on one page. To set the pageSize parameter, you should pass a value greater than 0 as a query argument.

For example, using the query below, you can paginate a list of backup serves, 1 backup server per page:

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=backupServer&pageSize=1    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

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

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
