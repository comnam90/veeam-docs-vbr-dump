---
title: "Step 2. Add Worker Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_worker_configuration.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Add Worker Configuration


For Veeam Backup for Microsoft Azure to be able to launch worker instances in the private environment, create a worker configuration in the same Azure region where the protected VM resides, as described in section [Adding Worker Configurations](azure_worker_configuration_add.md). When creating the configuration, make sure to select a VNet for the worker instances.

|  |
| --- |
| Important |
| If you plan to protect Azure VMs that have [Ultra Disks](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-enable-ultra-ssd?tabs=azure-portal) or [Premium SSD v2 disks](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-deploy-premium-v2?tabs=azure-cli) attached and you created the private DNS zones manually at [step 1](azure_app_pne_dns_zones.md), you must create the worker configuration in the same Azure subscription where the private DNS zones reside. |

Page updated 2026-03-13

