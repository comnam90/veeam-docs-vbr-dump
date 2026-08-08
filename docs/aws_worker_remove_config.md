---
title: "Removing Configurations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_worker_remove_config.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Configurations


The backup appliance allows you to permanently remove worker configurations if you no longer need them. When you remove a worker configuration, the backup appliance does not remove currently running worker instances that have been created based on this configuration — these instances are removed only when the related operations complete.

To remove a worker configuration from the backup appliance, do the following:

1. Switch to the Configuration page.
2. Navigate to Workers > Network.
3. Switch to the necessary tab.
4. Select the worker configuration and click Remove.

|  |
| --- |
| Note |
| If there are any worker instances created based on the selected configuration that are currently involved in a backup or restore process, these instances will be removed only when the process completes. |

[![Removing Worker Configurations](images/aws_remove_worker_configuration.webp)](images/aws_remove_worker_configuration.webp "Removing Worker Configurations")

Page updated 2026-05-20

