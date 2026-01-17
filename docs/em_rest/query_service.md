---
title: "Queries"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/query_service.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Some of the Veeam Backup Enterprise Manager resources support request query parameters. Using query, you can:

* Perform ad-hoc search for necessary resources
* Filter results by defined criteria
* Define the format of results (type of the resource representation), sorting options, and pagination

|  |
| --- |
| Tip |
| To learn what query parameters are available for a specific resource, see the Query Parameters section in the GET HTTP method description of the resource. For example, [GET /backupServers/{ID}](get_backupservers_id.md). |

Query Syntax

In Veeam Backup Enterprise Manager REST API, the query component is added to the base URL. The query string has the following format:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/query?type=<QueryType>[&ParamName=ParamValue] |

where:

* http://<EnterpriseManager>:9399/api/ is the base URL for Veeam Backup Enterprise Manager REST API.
* query? identifies the beginning of the query string. The query? element is added to the base URL.
* type=<QueryType> defines the resource type for which the query is executed, for example, type=BackupServer or type=Job.

For details, see [Type Parameter](#type).

* [&ParamName=ParamValue]contains filter parameters passed to the query, for example, format=entities.

For details, see [Optional Parameters](#optional).

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
