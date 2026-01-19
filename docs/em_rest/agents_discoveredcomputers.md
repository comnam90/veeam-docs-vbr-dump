---
title: "/agents/discoveredComputers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_discoveredcomputers.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /agents/discoveredComputers


Represents a list of all protected computers in all protection groups configured on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/discoveredComputers |

Related Resources

[/agents/discoveredComputers/{ID}](agents_discoveredcomputers_id.md)

Methods

The following methods are supported for the /agents/discoveredComputers resource:

[GET /agents/discoveredComputers](get_agents_discoveredcomputers.md)

Resource Representation

The /agents/discoveredComputers resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |


