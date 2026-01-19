---
title: "/querySvc"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/querysvc.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /querySvc


Represents a query service that you can use to filter, sort and paginate results returned by the REST API.

The /querySvc resource provides a set of query links. By following a link from the list, the client executes a query and gets a list of resources of a specific type, paginated, and sorted in the ascending order. For example, the client can get a list of job entities, 15 per page, displayed in the ascending order. Additionally, the /querySvc resource provides a link to the current logon session.

The queries in the /querySvc resource representation are preconfigured. You can use the provided queries or construct your own query requests with custom criteria. For details, see [Queries](query_service.md#syntax).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/querySvc |

Related Resources

None.

Methods

The following methods are supported for the /querySvc resource:

[GET /querySvc](get_querysvc.md)

Resource Representation

The /querySvc resource has a resource representation of the following type:

|  |
| --- |
| <QuerySvc xmlns="http://www.veeam.com/ent/v1.0" Type="QueryService" Href="https://localhost:9398/api/querySvc"> |


