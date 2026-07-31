---
title: "/tasks"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tasks.html"
last_updated: "2026"
product_version: "13.1.0.411"
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
| <Tasks xmlns="http://www.veeam.com/ent/v1.0">   <Task Type="Task" Href="https://localhost:9398/api/tasks/task-29">     <Links>       <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-29" />     </Links>     <TaskId>task-29</TaskId>     <State>Finished</State>     <Operation>StartRebuildScope</Operation>     <Result Success="true" />   </Task>   <Task Type="Task" Href="https://localhost:9398/api/tasks/task-30">     <Links>       <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-30" />     </Links>     <TaskId>task-30</TaskId>     <State>Finished</State>     <Operation>StartJob</Operation>     <Result Success="true">       <Message>Job "SQL Server Replication" triggered to start.</Message>     </Result>   </Task> </Tasks> |

Page updated 2026-07-29

