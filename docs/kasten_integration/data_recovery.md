---
title: "data_recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/data_recovery.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

Veeam Plug-In for Kasten offers the following recovery options for various disaster recovery scenarios:

* [Restoring to Kubernetes](restoring_kasten.md)

Restores applications to the Kubernetes cluster (using the Veeam Kasten web console).

* [Exporting Disks](export_disks.md)

Restore persistent disks from backups and convert them to disks in the VMDK, VHD or VHDX format.

* [Instant First Class Disk (FCD) Recovery](fcd_disk_recovery.md)

Recover persistent disks from backup files and register them as First Class Disks (FCDs).

* [Restoring Guest OS Files](guest_file_recovery.md)

Recover individual guest OS files from Linux file systems.

* [Exporting Backup Files](export_backups.md)

Synthesize an independent full backup file using restore points that are located in your Veeam backup repositories.

|  |
| --- |
| Important |
| Consider the following:   * Veeam Plug-In for Kasten does not allow you to restore Kubernetes containers from a Veeam Backup & Replication server to a Veeam Kasten cluster or any other location. To perform the restore operations with Kubernetes containers, use Veeam Kasten recovery options. For more information, see [Veeam Kasten Docs](https://docs.kasten.io/latest/usage/restore.html). * You can perform the recovery options (except restore to the Kubernetes cluster) only for restore points exported to the Veeam backup repository. * Restore points created by backup copy jobs or tape jobs can be recovered only by using operations available in the Veeam Backup & Replication console. You cannot use Veeam Kasten recovery options. |

Page updated 8/26/2024

Page content applies to build 13.0.1.1071
