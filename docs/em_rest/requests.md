---
title: "Requests"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/requests.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Requests


For requests, the client can use the following standard HTTP methods:

* [POST](post_method.md) (Create) — creates a new resource
* [GET](get_method.md) (Read) — retrieves information about the resource — the resource representation
* [PUT](put_method.md) (Update) — makes changes to a resource
* [DELETE](delete_method.md) (Delete) — removes a resource

In some cases, the same HTTP method can be used to perform different kinds of actions with the resource. For example, using the POST HTTP method, you can add objects to the job, start a job, stop, retry, clone or disable it. To identify the action that will be performed with the resource, Veeam Backup Enterprise Manager REST API adds the name of the action to the end of the action URL, for example:

|  |
| --- |
| <Link Rel="Start" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?action=start" /> |

Additionally, the action is described with the Rel attribute within the link, for example:

|  |
| --- |
| <Link Rel="Edit" Type="JobReference" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5" Name="Exchange Backup" /> |

The table below describes relations between the operations that the client can perform with resources and HTTP verbs to be used:

| Operation | HTTP Verb | Sample Actions |
| --- | --- | --- |
| Create | POST | Create a new resource, for example, a logon session or credentials record. |
| Delete | DELETE | Delete a resource, for example, a logon session or a task. |
| Alternate | GET | Get an entity representation or a reference representation for the resource. |
| Edit | PUT | Edit a resource, for example, a job. |
| Start | POST | Start some operation, for example, a job. |
| Test | POST | Test a cloud failover plan. |
| Stop | POST | Stop some operation, for example, a job. |
| Retry | POST | Retry some operation, for example, a job. |
| Clone | POST | Clone a resource, for example, a job. |
| Related | GET | Get a resource representation of the resource related to the current one, for example, a list of VM restore points related to the catalog VM restore point. |
| Restore | POST | Perform a restore operation, for example, entire VM restore. |
| Failover | POST | Perform VM replica failover. |
| Download | POST | Download a file. |
| ToggleScheduleEnabled | POST | Enable or disable job launch by the schedule. |
| ToggleRestoreScopesEnabled | POST | Enable or disable restore scope settings for the account having a specific role in Veeam Backup Enterprise Manager. |
| Browse | POST | Launch the browsing operation for the VM file system. |
| Up | GET | Retrieve a list of resources that are parent to the current resource, for example: backup server parent for a job resource. |
| Down | GET | Retrieve a list of resources that are child to the current resource, for example: job sessions child for a job resource. |
| Previous | GET | Move back to the previous page with query results |
| Next | GET | Move forward to the next page with query results |
| First | GET | Move to the first page with query results |
| Last | GET | Move to the last page with query results |


