---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


When you plan to use Veeam Plug-in for Xen, keep in mind the following limitations and considerations.

Configuration

When configuring Veeam Plug-in for Xen, consider the following:

* The Xen pool must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.
* After you make changes to your Xen environment (for example, you migrate a VM between hosts in a pool), these changes may not appear in Veeam Backup & Replication immediately. The data synchronization process between the backup server and the Xen pool may take up to 15 minutes to complete. You can speed up the data synchronization process by [rescanning the Xen pool](xen_server_rescan.md).
* If a different pool node becomes a pool coordinator then the one specified during initial configuration, all further pool operations are suspended. To fix it, replace the connected pool coordinator as described in section [Step 2. Specify Domain Name or IP Address of XCP-ng Pool Coordinator](xen_xcp_server_add_name.md) or [Step 2. Specify Domain Name or IP Address of Citrix XenServer Pool Coordinator](xen_server_add_name.md). To prevent future issues, do one of the following:

* Install a self-signed certificate with all pool host IPs specified as alternative names of cluster nodes.
* If every pool host already has a certificate, add them as trusted in Veeam Backup & Replication in advance.

Workers

When configuring workers, consider the following:

* Veeam Plug-in for Xen requires at least one worker deployed in the same pool where protected VMs reside.

* The worker image is stored in the storage repository where it was initially uploaded.

Backup

When protecting Xen resources, consider the following:

* Veeam Plug-in for Xen does not support VM replication.
* Veeam Plug-in for Xen does not support guest quiescence.
* Veeam Plug-in for Xen does not support RAW disk processing. To back up VMs with RAW disks, manually exclude these disks as described in section [Step 3. Configure Backup Source Settings](xen_backup_job_create_assign_vms.md).
* HotAdd is not supported for storage repositories hosted on SMAPIv3 protocol.
* NBD backup transport is supported. It requires OpenSSL version 3.0.9, is not enabled by default and is highly dependant on network configuration. To avoid further issues related to NBD, we recommend that you deploy a dedicated worker on each host.
* When a backup snaphot is created, Veeam Plug-in for Xen renames it following its own naming convention. In some cases, API returns a success response while the renaming operation has failed, which results in orphaned snapshots.
* When managing backup repositories, consider that Veeam Plug-in for Xen does not support storing backups in Veeam Cloud Connect repositories. However, you can use them for [storing copies of backups](xen_backups_copy.md) created with Veeam Plug-in for Xen.

Restore

When restoring Xen resources, consider the following:

* In case of restore to original location, Veeam Plug-in for Xen is unable to preserve the original VM disk IDs which results in the next incremental backup creating another full backup. Note that if disk exclusions were configured for the original VM, these settings need to be reapplied due to the new disk IDs.
* Restore to Xen from other platform and backup agent backups may fail unless a default VM template is defined for the target pool.
* Due to the Xen limitations, restore of a QCOW2 disk to an SMB storage repository fails and leaves the disk on a datastore making further repository rescan operations impossible. To fix it, you can delete the QCOW2 disk from the repository by directly accesssing pool coordinator through SSH.
* Xen Orchestra ancillary metadata is not restored during normal restore operations.
* During restore to a new location, VM names longer than 80 characters are truncated.

Page updated 2026-07-30

