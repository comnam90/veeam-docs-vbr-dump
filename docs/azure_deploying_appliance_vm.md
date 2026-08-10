---
title: "Step 5. Specify VM Instance Name and Description"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_deploying_appliance_vm.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify VM Instance Name and Description


At the Virtual Machine step of the wizard, specify a name and description for the Azure VM on which the backup appliance will be deployed. Note that the name must meet the[Microsoft Azure resource name rules](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/resource-name-rules#microsoftcompute).

|  |
| --- |
| Tip |
| By default, Veeam Backup & Replication uses the minimum recommended B2ms VM size for the backup appliance. If you want to choose a specific VM size, click Choose VM size (optional) and select the necessary size in the VM Size window.  For the list of recommended VM sizes, see [Sizing and Scalability Guidelines](azure_sizing_appliance.md). Keep in mind that in Veeam Backup for Microsoft Azure version 13, you can only choose the B2ms, F4s\_v2 or F8s\_v2 VM size. |

![Step 5. Specify VM Instance Name and Description](images/azure_add_new_azure_apl_vm.webp)

Page updated 2026-07-01

