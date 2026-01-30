---
title: "Step 5. Specify vApp Processing Order"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_cdp_policy_order.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Step 5. Specify vApp Processing Order


At the vApps step of the wizard, click Up and Down to change the processing order. VM containers (vApps, organization, organization VDCs, and so on) at the top of the list have a higher priority and will be processed first.

|  |
| --- |
| Note |
| Consider the following:   * VMs inside a VM container are processed at random. * To ensure that vApps are processed in the specified order, you must add them as standalone vApps, not as a part of containers. * The processing order may differ from the order that you have specified. For example, if resources of a vApp that is higher in the priority are not available, and resources of a vApp that is lower in the priority are available, Veeam Backup & Replication will process the vApp with the lower priority first. |

![Step 5. Specify vApp Processing Order](images/vcd_cdp_policy_order.webp)


