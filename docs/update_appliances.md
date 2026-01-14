---
title: "Updating Veeam Appliances"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/update_appliances.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Updating Veeam Appliances

In this article

Update operations are managed by Veeam Updater — a Veeam service that runs on backup server or other backup infrastructure components deployed from Veeam appliances — Veeam Software Appliance and Veeam Infrastructure Appliance. The service communicates with components through Veeam Backup & Replication REST API and uses the Veeam Identity Service for authorization.

The following updates can be installed:

* Operating system and security updates — mandatory, installed automatically and cannot be skipped or canceled.
* Veeam Backup & Replication security updates — mandatory, installed automatically and cannot be skipped or canceled.
* Veeam Backup & Replication updates including major releases, minor releases and private fixes — optional.

You can access Veeam Updater in the following ways:

* In the Veeam Host Management console, click Updates in the management pane.
* In the Veeam Backup & Replication web UI, click About in the management pane. Then, click the Updater interface link in the Product Information section.
* In the Veeam Backup & Replication console, click Updates > Check for Updates in the main menu. Alternatively, you can click Updates > Missing Updates in the main menu and click the name of the server.

In This Section

* [How Updates Work](update_appliance_hiw.md)
* [Configuring Updates](update_appliance_configure_updates.md)
* [Checking Updates](update_appliance_check_updates.md)
* [Installing Updates](update_appliance_install_updates.md)
* [Viewing Update History](update_appliance_view_history.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
