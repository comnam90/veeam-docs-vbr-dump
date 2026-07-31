---
title: "Step 2. Specify NetApp Server Name or Address and Storage Role"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/netapp_add_name.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Specify NetApp Server Name or Address and Storage Role


At the Name step of the wizard, specify the storage system name, description and storage role.

1. In the Management server DNS name or IP address field, specify a DNS name, or IPv4 or IPv6 address of the storage system. Note that you can use IPv6 addresses only if IPv6 communication is enabled as described in the [IPv6 Support](ipv6.md) section in the Veeam Backup & Replication User Guide.

You can add either the entire NetApp cluster or a specific Storage Virtual Machine (SVM). If you add an SVM, check [NetApp ONTAP Limitations](storage_limitations_netapp.md).

1. In the Description field, provide a description for future reference. The default description contains information about the user who added the storage system, date and time when the storage system was added.
2. In the Role section, select the types of backup jobs that are allowed to access this storage system:

1. Select the Block or file storage for VMware vSphere check box to allow VMware backup.
2. Select the Block storage for Microsoft Windows servers check box to allow backup of Veeam Agents.
3. Select the NAS filer check box to allow NAS backup.

This is the only available option for the Linux-based backup server.

1. Select the NDMP server check box to allow file backup to tape jobs from this storage system using SMTape functionality.

To enable this feature, once the NetApp server is added to the backup infrastructure, you must add it as an NDMP server following the steps of the [New NDMP Server](adding_ndmp_servers.md) wizard. For more information, see [NetApp NDMP Server Backup to Tape](netapp_ndmp.md).

When you select the Block or file storage for VMware vSphere, or Block storage for Microsoft Windows server, or NAS filer check boxes, additional steps of the wizard will appear.

If you do not select any check box, Veeam Backup & Replication displays an error. To proceed with the wizard, select at least one check box.

![Step 2. Specify NetApp Server Name or Address and Storage Role](images/netapp_add_name.webp)

Page updated 2026-07-02

