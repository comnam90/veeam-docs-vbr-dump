---
title: "Removing Worker Configurations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_worker_configuration_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Worker Configurations


The backup appliance allows you to permanently remove worker configurations if you no longer need them. When you remove a worker configuration, the backup appliance does not remove currently running worker instances that have been created based on this configuration — these instances are removed only when the related operations complete.

To remove a worker configuration from the backup appliance, do the following:

1. Switch to the Configuration page.
2. Navigate to Workers > Network.
3. Select the worker network configuration and click Remove.

[![Removing Worker Configuration](images/azure_remove_worker_configuration.webp)](images/azure_remove_worker_configuration.webp "Removing Worker Configuration")

Page updated 2026-07-01

