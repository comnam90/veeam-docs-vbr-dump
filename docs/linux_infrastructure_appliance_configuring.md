---
title: "Configuring Veeam Infrastructure Appliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/linux_infrastructure_appliance_configuring.html"
last_updated: "10/8/2025"
product_version: "13.0.1.1071"
---

# Configuring Veeam Infrastructure Appliance

In this article

The Host Management console is used to configure Veeam Infrastructure Appliance. For more information, see [Configuring Veeam Appliances](hmc.md).

|  |
| --- |
| Note |
| Note that if you enable the web UI on a hardened repository created with the Veeam Infrastructure Appliance, it will be automatically disabled after 24 hours. |

In addition to the standard options, the Host Management console for a Veeam Infrastructure Appliance can be used to generate a pairing code.

The first time you add a specific Veeam Infrastructure Appliance component to Veeam Backup & Replication, a connection is automatically established. If you later add the component to a different Veeam Backup & Replication installation, you must first delete the previous connection and generate a pairing code.

To do this, do one of the following:

* If you use the Veeam Host Management web UI, do the following:

1. In the main menu, click Backup Infrastructure.
2. Click Remove.
3. Click Create a new pairing code.

* If you use the Veeam Host Management TUI, do the following:

1. In the main menu, highlight Integration settings.
2. Press [Delete] to delete the previous connection.
3. Press [F1] to generate a pairing code.

Page updated 10/8/2025

Page content applies to build 13.0.1.1071
