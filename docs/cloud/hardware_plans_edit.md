---
title: "Editing Hardware Plan Settings"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/hardware_plans_edit.html"
last_updated: "10/14/2025"
product_version: "13.0.1.1071"
---

# Editing Hardware Plan Settings


You can edit settings of hardware plans you have configured.

|  |
| --- |
| Note |
| When Veeam Backup & Replication saves new hardware plan settings to the configuration database, resources provided to tenants through the edited hardware plan will become temporarily unavailable to tenants. VM replicas in Failover state after partial site failover will also become temporarily inaccessible. |

To edit settings of a hardware plan:

1. Open the Cloud Connect view.
2. In the inventory pane, click the Replica Resources node.
3. Do one of the following:

* Select the necessary hardware plan in the working area and click Edit Plan on the ribbon or right-click the necessary hardware plan and select Edit.
* Select the necessary hardware plan in the inventory pane and click Edit Plan on the ribbon or right-click the necessary hardware plan and select Edit.

1. Edit hardware plan settings as required.

|  |
| --- |
| Note |
| You cannot reduce the number of networks with internet access and the number of internal networks in the hardware plan when editing hardware plan settings. |

[![Edit Hardware Plan](images/hardware_plan_edit.webp)](images/hardware_plan_edit.webp "Edit Hardware Plan")


