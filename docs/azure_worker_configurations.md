---
title: "Managing Worker Configurations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_worker_configurations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Worker Configurations


A configuration is a group of network settings that the backup appliance uses to launch worker instances in a specific Azure region to perform data protection and disaster recovery operations. The backup appliance launches one worker instance per each Azure resource added to a backup policy or restore task.

By default, Veeam Backup for Microsoft Azure automatically creates a new network configuration for each Azure region in which it launches worker instances. However, you can add custom worker configurations to provide network settings that will be used to launch worker instances in a specific region.

|  |
| --- |
| Important |
| Consider the following:   * For each automatically created worker configuration, Veeam Backup for Microsoft Azure creates a virtual network, a subnet and a network security group. * It is not recommended that you manually change settings of automatically created configurations. If you want to use a specific worker configuration, add it manually as described in section [Adding Worker Configurations](azure_worker_configuration_add.md). |

In This Section

* [Specifying Destination for Worker Instances](azure_worker_service_account.md)
* [Adding Worker Configurations](azure_worker_configuration_add.md)
* [Editing Worker Configurations](azure_worker_configuration_edit.md)
* [Removing Worker Configurations](azure_worker_configuration_remove.md)

Page updated 2026-07-01

