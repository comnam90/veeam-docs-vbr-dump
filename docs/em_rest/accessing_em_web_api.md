---
title: "accessing_em_web_api"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/accessing_em_web_api.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

To access Veeam Backup Enterprise Manager REST API, send the GET HTTP request to its base URL. The base URL is https://<Enterprise-Manager>:9398/api/, where:

* <Enterprise-Manager> is the name of the server on which Veeam Backup Enterprise Manager is installed.
* 9398 is the HTTPS communication port. HTTP port 9399 is obsolete and is not used in version 1.5 of Veeam Backup Enterprise Manager REST API.

If you specified another port for communication over HTTPS during the Veeam Backup Enterprise Manager installation, adjust the port number in the URL as required.

|  |
| --- |
| GET https://localhost:9398/api/ |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
