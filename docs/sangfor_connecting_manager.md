---
title: "Connecting Sangfor aSV Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_connecting_manager.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Connecting Sangfor aSV Server


A Sangfor aSV server is a Sangfor Cloud Platform instance that allows the backup server to access Sangfor aSV resources such as clusters, VMs, storage and networks. After you add a Sangfor aSV server to the backup infrastructure, you will be able to deploy workers and to manage data protection tasks for Sangfor aSV VMs.

Considerations and Limitations

After you add a Sangfor Cloud Platform to the backup infrastructure, consider the following:

* If you register a new cluster with the Sangfor Cloud Platform, Veeam Backup & Replication will automatically add it to the backup infrastructure and you will be able to protect resources in this cluster. For more information, see sections [Performing Backup](sangfor_data_protection.md) and [Performing Restore](sangfor_data_recovery.md).
* If you unregister an existing cluster from the Sangfor Cloud Platform, you will not be able to protect resources in this cluster anymore.

In This Section

* [Adding Sangfor aSV Server to Backup Infrastructure](sangfor_server_add.md)
* [Editing Sangfor aSV Server Properties](sangfor_server_edit.md)
* [Rescanning Sangfor aSV Server](sangfor_server_rescan.md)
* [Removing Sangfor aSV Server](sangfor_server_remove.md)

Page updated 2026-07-16

