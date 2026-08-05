---
title: "Step 6. Specify Mount Server Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/add_data_cloud_vault_aws_mount.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Specify Mount Server Settings


[This step applies only if you plan to perform Instant Recovery, guest OS file restore and application item restore operations]

At the Mount Servers step of the wizard, you can specify servers that will be used to mount backed-up EC2 instance volumes and copy data to restore locations. Windows mount servers are required to restore data from Windows EC2 instances and Linux mount servers are required to restore data from Linux EC2 instances.

The backup server is automatically selected as the mount server for the operating system it is hosted on. For the other operating system, Veeam Backup & Replication selects a server from your backup infrastructure (if any) that meet the system requirements. However, you can also specify servers manually. To do that, select the necessary servers from the lists of available mount servers. For a server to be displayed in the Windows mount server or the Linux mount server list, it must be added to the backup infrastructure as described in [Adding Microsoft Windows Servers](add_windows_server.md) or [Adding Linux Servers](add_linux_server.md). If you have not added the server to Veeam Backup & Replication beforehand, you can do it without closing the New External Repository wizard. To do that, click Add new and complete the New Server wizard.

If you plan to use Instant Recovery or scan backups with SureBackup in VMware vSphere environments, you must specify additional settings. To do that, click Configure settings. In the Mount Server Settings window, do the following:

1. Select the Enable vPower NFS service on the mount server checkbox. The Veeam vPower NFS Service publishes backups to the ESXi host as an NFS datastore, allowing you to perform Instant Recovery of any backup (physical, virtual or cloud) to a VMware vSphere VM.

To customize network ports used by the Veeam vPower NFS Service, click Ports. By default, the service uses port 1058 to mount the vPower NFS datastore to the ESXi host and port 2049 to connect to the target NFS share.

|  |
| --- |
| Important |
| It is not recommended that you run Microsoft Windows NFS services and Veeam vPower NFS Service on the same mount server. Otherwise, both services may fail to work properly. |

1. [Applies only if you plan to perform Instant Recovery] In the Instant recovery write cache folder field, specify a folder on the mount server that will be used to store changed volume blocks of EC2 instances recovered during Instant Recovery. Make sure the disk that contains this folder has enough free space for these blocks.

![Step 6. Specify Mount Server Settings](images/external_vault_aws_mount.webp)

Page updated 2026-07-20

