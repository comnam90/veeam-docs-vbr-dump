---
title: "/tasks"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tasks.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /tasks


Represents a collection of all tasks created by Veeam Backup Enterprise Manager in response to client requests within the currently existing logon session.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/tasks |

Related Resources

[/tasks/{ID}](tasks_id.md)

Methods

The following methods are supported for the /tasks resource:

[GET /tasks](get_tasks.md)

Resource Representation

The /tasks resource has a resource representation of the following type:

|  |
| --- |
| <Tasks xmlns="http://www.veeam.com/ent/v1.0"> |


