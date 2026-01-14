---
title: "em_web_api_versions"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/em_web_api_versions.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Enterprise Manager REST API is available in multiple versions. Every later version adds support for new resources and operations that can be performed with them.

Veeam Backup Enterprise Manager REST API follows the release cycle of Veeam Backup & Replication. Generally, the latest version of REST API supports features introduced in the latest version of Veeam Backup & Replication.

To work with resources available in a specific version of Veeam Backup Enterprise Manager REST API, you must specify the version in the POST HTTP request to the /sessionMngr resource. For details, see [Perform Logon](logging_on.md).

The table below describes relations between versions of Veeam Backup Enterprise Manager REST API and Veeam Backup & Replication. The table also contains sample links to create a new logon session for a specific version.

The Deprecated support status is intermediate. Deprecated REST API versions are expected to become unsupported. You can still use them but it is recommended that you switch to a newer one.

| REST API Version | Support Status | Veeam Backup & Replication Version | Logon Session URL |
| --- | --- | --- | --- |
| 1.7 | Supported | 12 to 12.1 | https://<Enterprise-Manager>:9398/api/sessionMngr/?v=v1\_7  https://<Enterprise-Manager>:9398/api/sessionMngr/?v=latest |
| 1.6 | Deprecated | 11 to 11a | https://<Enterprise-Manager>:9398/api/sessionMngr/?v=v1\_6 |
| 1.5 | Deprecated | 10.0 to 10a | https://<Enterprise-Manager>:9398/api/sessionMngr/?v=v1\_5 |
| 1.4 | Not supported | 9.5 Update 4 to 9.5 Update 4b | — |
| 1.3 | Not supported | 9.5 to 9.5 Update 3 | — |
| 1.2 | Not supported | 9.0 to 9.0 Update 2 | — |
| 1.1 | Not supported | 8.0 to 8.0 Update 3 | — |

|  |
| --- |
| Tip |
| To create a logon session for the latest version of Veeam Backup Enterprise Manager REST API supported in the currently installed version of Veeam Backup & Replication, you can also use the following link: https://<Enterprise-Manager>:9398/api/sessionMngr/?v=latest. |

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
