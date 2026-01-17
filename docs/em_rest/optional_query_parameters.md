---
title: "Optional Parameters"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/optional_query_parameters.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---


In this article

The query parameters component [&ParamName=ParamValue] is an optional part of the query. Optional parameters are specified as ParamName=ParamValue pairs. Multiple ParamName=ParamValue pairs are separated with the ‘&’ (ampersand) character.

When building a query string, you can use the following optional query parameters:

* [format](format.md)
* [sortAsc, sortDesc](sortasc_sortdesc.md)
* [pageSize, page](pagesize_and_page.md)
* [filter](filter.md)

|  |
| --- |
| Important |
| The ParamName=ParamValue pair must be presented as a string of the [A-Za-z\_0-9] type without spaces. Stings containing spaces must be includes in quotes, for example: /query?type=job&filter=Name==”Fileserver Backup”. If the string contains spaces and is not included in quotes, the server will ignore spaces in the string.  If the string itself contains a quote character, the quote must be doubled. For example, if the job name is “Backup”, the query string will have the following format: /query?type=job&filter=Name==””Backup””. |

Example

Using the query below, you can get a list of all job entities sorted in the ascending order. This query contains two ParamName=ParamValue pairs:

* format=Entities — to display entities of resources, not references
* sortAsc=Name — to sort jobs in the ascending order by the Name parameter

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=job&format=Entities&sortAsc=Name    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 9/1/2023

Page content applies to build 13.0.1.1071
