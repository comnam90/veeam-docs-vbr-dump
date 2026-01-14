---
title: "http_response_codes"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/http_response_codes.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The request to the server can return a successful status or an error.

Success Operation Statuses

| Code | Applies to HTTP Method | Description | Response Body Content | Details |
| --- | --- | --- | --- | --- |
| 200 | GET  PUT | OK | Resource representation | The operation has been successfully completed. |
| 201 | POST | Created | Representation of the created resource | The resource has been successfully created. |
| 202 | POST  DELETE | Accepted | n/a | The request has been accepted and a task to handle the request has been created.  A 202 response is typically used for actions that take a long while to process or performed asynchronously. This response is accompanied by a task resource. |
| 204 | PUT  POST  DELETE | No Content | n/a | The request is valid and has been successfully completed; the response does not include a body.  A 204 status can be sent, for example, as a response to the DELETE HTTP request, informing that a resource has been deleted and has no representation. |

Error operation statuses

| Code | Applies to HTTP Method | Description | Response Body Content | Details |
| --- | --- | --- | --- | --- |
| 400 | POST  PUT | Bad Request | Error | The request body is malformed, incomplete or otherwise invalid. |
| 401 | All | Unauthorized | Error | The authorization header has been expected but not found (or found but is expired). |
| 403 | All | Forbidden | Error | The user sending a request does not have adequate privileges to access one or more objects specified in the request. |
| 404 | All | Not Found | Error | One or more resources specified in the request could not be found in the specified resource collection. |
| 405 | All | Method is not Allowed | Error | The HTTP method specified in the request is not supported for this resource. |
| 500 | GET  POST  PUT | Internal Server Error | Error | The request has been received but could not be completed because of an internal error at the server side. |
| 501 | POST  PUT  DELETE | Not Implemented | Error | The server does not support the functionality required to fulfill the request. |
| 503 | All | Service Unavailable | Error | The server is currently unable to handle the request due to a temporary overloading or maintenance of the server. |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
