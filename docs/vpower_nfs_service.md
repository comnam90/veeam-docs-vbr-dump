---
title: "Veeam vPower NFS Service"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vpower_nfs_service.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Veeam vPower NFS Service

In this article

The vPower technology enables the following features in the VMware vSphere environment:

* SureBackup
* SureReplica
* Instant Recovery
* Instant Disk Recovery
* Staged restore
* Guest OS file restore

The key component of the vPower technology is the vPower NFS Service (veeamnfssvc.service). This service is a Microsoft Windows or Linux service that runs on a machine and allows this machine to act as an NFS server.

On the vPower NFS server, Veeam Backup & Replication creates a special directory — the vPower NFS datastore. When you start a VM or a VM disk from a backup, Veeam Backup & Replication "publishes" VMDK files of the VM from the backup on the vPower NFS datastore. Technically, Veeam Backup & Replication emulates the presence of VMDK files on the vPower NFS datastore — the VMDK files themselves are still located in the backup file in the backup repository.

The vPower NFS datastore is mounted to the ESXi host. As a result, the ESXi host can access backed-up VM images with the help of the vPower NFS datastore and work with them as with regular VMDK files. The emulated VMDK files function as pointers to the real VMDK files in the backup repository.

The vPower NFS datastore stays mounted to the ESXi host. Each time you start an operation from the list, Veeam Backup & Replication checks whether vPower NFS datastore is mounted to the host. If you manually unmounted the datastore or the datastore was unmounted by other causes, Veeam Backup & Replication remounts the datastore.

|  |
| --- |
| Important |
| Veeam vPower NFS datastores are service datastores that can be used for vPower operations only. You cannot use them as regular VMware vSphere datastores — for example, you cannot place files of replicated VMs on such datastores. |

Consideration and Limitations

Consider the following:

* The vPower NFS server is installed on a mount server. For more information on the system requirements for the mount server, see [System Requirements](system_requirements.md#mount).
* [vPower NFS on Linux] Due to the [ports](used_ports.md#vpower) used by the vPower NFS service, it is not possible to configure a native NFS server on the same machine.

vPower NFS Server Location

If you store backups on a Microsoft Windows or Linux-based backup repository, it is strongly recommended that you enable the vPower NFS server on this backup repository. In this case, Veeam Backup & Replication will be able to set up a direct connection between the backup repository and ESXi to which the vPower NFS datastore is mounted.

The Veeam vPower NFS Service can also run on the backup server. However, in this case the recovery verification performance may decrease. The connection between the ESXi host and backup repository will be split into two parts:

1. From ESXi host to the vPower NFS server
2. From the vPower NFS server to the backup repository

vPower-Specific Settings

To establish a connection between the ESXi host and vPower NFS server, you must make sure that the ESXi host has a proper network interface configuration and can access the vPower NFS server.

When connecting to the vPower NFS server, the ESXi host uses a VMkernel interface. For this reason, the ESXi host must have a VMkernel interface. Otherwise, Veeam Backup & Replication will fail to mount the vPower NFS datastore on the ESXi host.

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
