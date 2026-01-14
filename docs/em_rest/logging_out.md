---
title: "logging_out"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/logging_out.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

To finish working with Veeam Backup Enterprise Manager REST API and log out:

1. Send the GET HTTP request to the /logonSessions resource to get a list of existing logon sessions:

|  |
| --- |
| Request:  GET https://localhost:9398/api/logonSessions    Response:  200 OK    Response Body:  <LogonSessions xmlns="http://www.veeam.com/ent/v1.0"> |

1. Examine the representation of the logon session and find a link to logon session deletion:

|  |
| --- |
| <Link Rel="Delete" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/695f7cda-e4a6-4d9c-9603-8a6b05693c57" |

1. Send the DELETE HTTP request to the obtained link:

|  |
| --- |
| Request:  DELETE https://localhost:9398/api/logonSessions/695f7cda-e4a6-4d9c-9603-8a6b05693c57    Response:  204 No Content |

1. If you are using Veeam Backup Enterprise Manager Web Client, close the browser window.

The logon session will be deleted.

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
