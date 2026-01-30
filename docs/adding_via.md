---
title: "Adding Veeam Infrastructure Appliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/adding_via.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Adding Veeam Infrastructure Appliance


You must add to the backup infrastructure Veeam Infrastructure Appliances that you plan to use as backup infrastructure components for various types of backup and restore operations.

Before you add a Veeam Infrastructure Appliance, configure the machine with Veeam Infrastructure Appliance based on the JeOS ISO file. For more information, see [Installing Veeam Infrastructure Appliance with ISO](linux_infrastructure_appliance_install.md).

You can add Veeam Infrastructure Appliance, Veeam Infrastructure Appliance (with iSCSI & NVMe/TCP) or Veeam Hardened Repository. When you add a specific Veeam Infrastructure Appliance component to Veeam Backup & Replication, a connection is automatically established. No user name or password is required; authentication is performed using certificates. If you later add the component to a different Veeam Backup & Replication installation, you must first delete the previous connection and generate a pairing code. For more information, see [Configuring Veeam Infrastructure Appliance](linux_infrastructure_appliance_configuring.md).

|  |
| --- |
| Note |
| Veeam Infrastructure Appliance version is compatible with the same or later version of Veeam Backup & Replication. |

Related Topics

* [Adding Veeam Infrastructure Appliances Using Console](adding_via_console.md)
* [Adding Veeam Infrastructure Appliances Using Web UI](adding_via_web.md)


