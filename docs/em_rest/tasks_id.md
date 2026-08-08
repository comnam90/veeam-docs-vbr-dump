---
title: "/tasks/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tasks_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /tasks/{ID}


Represents a task having the specified ID. The task is created by Veeam Backup Enterprise Manager in response to client requests.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/tasks/{ID} |

Related Resources

[/tasks](tasks.md)

Methods

The following methods are supported for the /tasks/{ID} resource:

* [GET /tasks/{ID}](get_tasks_id.md)
* [DELETE /task/{ID}](delete_task_id.md)

Resource Representation

The /tasks/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-30">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-30" />   </Links>   <TaskId>task-30</TaskId>   <State>Finished</State>   <Operation>StartJob</Operation>   <Result Success="true">     <Message>Job "SQL Server Replication" triggered to start.</Message>   </Result> </Task> |

Page updated 2026-07-29

