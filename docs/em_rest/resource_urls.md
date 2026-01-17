---
title: "Resource URLs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/resource_urls.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Resource URLs


Every resource and resource collection in Enterprise Manager REST API has its own URL. A resource URL functions as a reference to an Enterprise Manager object: it is a resource address that the client can use to access the resource. For example, a backup server connected to Enterprise Manager can be addressed by the URL of the following type:

|  |
| --- |
| https://localhost:9398/api/backupServers/69368052-f7be-4be2-83d7-00ce2bbd7c0a |

Every resource URL consists of two parts:

* Base URL of Veeam Backup Enterprise Manager REST API
* Resource location

Base URL

The base URL is common for all resources: it is the entry point to Veeam Backup Enterprise Manager REST API. Veeam Backup Enterprise Manager REST API has the following base URL:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/ |

where:

* <Enterprise-Manager> is the name of the machine on which Veeam Backup Enterprise Manager is installed.
* 9398 is an HTTPS port used to communicate with the REST API web service.

In earlier versions of Veeam Backup & Replication, you could also access Veeam Backup Enterprise Manager REST API over the HTTP protocol using port 9399. This protocol is deprecated as insecure and is not used in version 1.5 of Veeam Backup Enterprise Manager REST API.

Resource Location

The resource location identifies the path to the resource itself in Enterprise Manager REST API. The resource location is suffixed to the base URL, forming the URL for the resource. For example, you can access the collection of jobs by the URL of the following type:

|  |
| --- |
| https://localhost:9398/api/jobs |

The resource location for key resources includes the entity ID. Every key resource has an entity ID — an object identifier in the URN format. The entity ID is unique and persists for the time of the Veeam Backup Enterprise Manager REST API work session. For example, a backup server connected to Veeam Backup Enterprise Manager can have the following entity ID and the following URN:

|  |
| --- |
| https://localhost:9398/api/backupServers/21a631e0-af7f-46ba-afbd-273de2e6fd4a |

Non-key resources may or may not have IDs that are called resource IDs. For example, the task resource has a resource ID of the following format:

|  |
| --- |
| https://localhost:9398/api/tasks/task-1 |

Such resources as files or directories do not have IDs:

|  |
| --- |
| https://localhost:9398/api/vmRestorePoints/e2b02b57-42dd-404a-b8af-8e45a58c1a88/mounts/1/C:/pagefile.sys |

|  |
| --- |
| Important |
| The client must never construct URLs for resources itself. URLs for all resources and actions that the client can perform are generated automatically by the server and provided in [resource representations](resource_representations.md). The client should only select the URL it needs and [send a necessary HTTP request](http_requests_and_responses.md) to it. |


