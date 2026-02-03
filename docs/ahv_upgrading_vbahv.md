---
title: "Upgrading to Veeam Plug-In for Nutanix AHV 9"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_upgrading_vbahv.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Upgrading to Veeam Plug-In for Nutanix AHV 9


You can upgrade Veeam Plug-in for Nutanix AHV from version 7.1 or 8 to version 9.

|  |
| --- |
| Important |
| To upgrade Veeam Backup for Nutanix AHV version 4.0, 4a, 5.0, 5.1, 6, 6.1 and 7 to version 9, you must first upgrade it to version 7.1 as described in the Veeam Backup for Nutanix AHV 7 User Guide, section [Upgrading to Veeam Backup for Nutanix AHV 7.1](https://helpcenter.veeam.com/archive/vbahv/7/userguide/upgrading_vbahv.html). |

Before you start the upgrade process, do the following:

* [Applies only to Veeam Plug-in for Nutanix AHV version 7.1] Upgrade your Veeam Backup & Replication server to version 12.3.1 or 12.3.2 as described in the Veeam Backup & Replication User Guide, section [Upgrading to Veeam Backup & Replication 12](https://helpcenter.veeam.com/docs/backup/vsphere/upgrade_vbr.html?ver=120).
* Download Veeam Backup & Replication version 13.0.1 from the [Veeam downloads page](https://www.veeam.com/backup-replication-download.html).
* [Applies only to Veeam Plug-in for Nutanix AHV version 7.1] Make sure the Nutanix AHV backup appliance is powered on.

To upgrade Veeam Plug-in for Nutanix AHV to version 9, do the following:

1. Upgrade your Veeam Backup & Replication server to version 13.0.1 as described in section [Upgrade and Update](vbr_updating.md).
2. Complete the Components Update wizard as described in section [Server Components Upgrade](components_update.md).

After the upgrade process completes, you can switch from the standalone cluster deployment to the [Prism Central deployment](ahv_infrastructure_prism_central.md). To do that, add the Prism Central to the backup infrastructure as described in section [Adding Nutanix AHV Server](ahv_add_ahv_cluster.md).

|  |
| --- |
| Note |
| [Applies only to Veeam Plug-in for Nutanix AHV version 7.1] Since Veeam Plug-in for Nutanix AHV version 9 comes without the backup appliance component, Veeam Backup & Replication will automatically import all the existing configuration settings of your current appliance to the Veeam Backup & Replication configuration database and then remove the backup appliance VM from the Nutanix cluster as soon as the upgrade process completes successfully. If the appliance was used to deliver backup traffic, Veeam Backup & Replication will also deploy a new worker VM and configure all the necessary settings required to perform backup and restore operations — you will be able to adjust these settings later when configuring Veeam Plug-in for Nutanix AHV as described in section [Editing Workers](ahv_workers_edit.md). |


