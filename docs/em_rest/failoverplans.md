---
title: "/failoverPlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/failoverplans.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /failoverPlans


Represents a collection of failover plans configured on backup servers that are connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Note |
| The /failoverPlans resource represents only regular failover plans configured on a backup server managed by Veeam Backup Enterprise Manager. Cloud failover plans configured by tenants whose accounts are created on a backup server appear in the /cloud/cloudFailoverPlans resource representation. |

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/failoverPlans |

Related Resources

[/failoverPlans/{ID}](failoverplans_id.md)

Methods

The following methods are supported for the /failoverPlans resource:

[GET /failoverPlans](get_failover_plans.md)

Resource Representation

The /failoverPlans resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


