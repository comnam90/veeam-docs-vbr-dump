---
title: "Editing Worker Configurations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_worker_configuration_edit.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Worker Configurations


For each worker configuration, you can modify settings specified while adding the worker configuration to the backup appliance:

1. Switch to the Configuration page.
2. Navigate to Workers > Network.
3. Select the worker network configuration and click Edit.
4. Complete the Edit Worker Network Configuration wizard:

1. To choose another virtual network and subnet for the related worker instances, to change the security group associated with the specified subnet, and to choose whether you want Veeam Backup for Microsoft Azure to assign public IP addresses to worker instances used for file-level recovery operations, follow the instructions provided in section [Adding Worker Configurations](azure_worker_configuration_network.md) (step 3).
2. At the Summary step of the wizard, review configuration information and click Finish to confirm the changes.

|  |
| --- |
| Note |
| If there are any worker instances created based on the selected configuration that are currently involved in a backup or restore process, the changes will be applied only when the process completes. |

[![Editing Worker Configuration](images/azure_edit_network_configuration.webp)](images/azure_edit_network_configuration.webp "Editing Worker Configuration")

Page updated 2026-07-01

