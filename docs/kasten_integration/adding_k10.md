---
title: "Adding Kasten Instance"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/adding_k10.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

Veeam Plug-In for Kasten allows you to view and manage Kasten policies as well as perform data protection and data recovery operations with exports created by Kasten from the Veeam Backup & Replication console. To do it, you must add the Kasten instance to the Veeam Backup & Replication infrastructure.

After you add the Kasten instance to the Veeam Backup & Replication infrastructure, Veeam Plug-In for Kasten accesses Veeam Kasten and synchronizes the following information:

* Kasten policies.
* Snapshots and exports created by Kasten policies.
* Snapshots and exports created manually.
* Sessions for the last 24 hours.

After synchronization is completed, Veeam Plug-In for Kasten shows this information in the Veeam Backup & Replication console and performs incremental syncs every 5 seconds to get updates.

To add the Kasten instance to Veeam Backup & Replication infrastructure, do the following:

1. [Launch the New Kasten Instance wizard](k10_launch.md).
2. [Specify the Kasten instance name](k10_name.md).
3. [Specify credentials](k10_credentials.md).
4. [Apply Settings](k10_apply.md).
5. [Finish working with the wizard](k10_finish.md).

Page updated 8/26/2024

Page content applies to build 13.0.1.1071
