---
title: "DELETE Method"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/delete_method.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# DELETE Method


The DELETE HTTP method is used to delete a resource to whose URL the client sends a request. In case of success, the DELETE HTTP method returns the HTTP response code 204 No Content.

In the example below, the DELETE HTTP request is used to delete the current logon session:

|  |
| --- |
| Request:  DELETE https://localhost:9398/api/logonSessions/0e879be7-8854-4a54-990b-ec16e1c6d1ee    Response:  204 No Content |


