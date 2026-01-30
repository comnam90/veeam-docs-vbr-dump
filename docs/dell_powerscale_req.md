---
title: "Dell Powerscale"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/dell_powerscale_req.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Dell Powerscale


To provide proper integration of Veeam Backup & Replication with Dell PowerScale (formerly Isilon) to implement the NAS backup functionality, consider the following:

* The Dell PowerScale system must be licensed for SnapshotIQ. Otherwise NAS integration will not work.
* The PowerScale service account is used to add the Dell PowerScale system to Veeam Backup & Replication, as described in [Adding Dell PowerScale](dell_powerscale_add.md). This account is used only for registering the storage system in the backup infrastructure and further storage rescans. You cannot use it for NAS file share backup and restore.

* Starting from Dell PowerScale 9.5, Veeam Backup & Replication supports SmartConnect.

* We recommend that you create a custom VeeamStorageIntegration role to group all necessary privileges. This role must be created in the System access zone. For more information on access zones, see the [Dell documentation](https://infohub.delltechnologies.com/sv-se/l/powerscale-onefs-nfs-design-considerations-and-best-practices-3/access-zone-23/).

Add the following privileges to the VeeamStorageIntegration role:

| Privilege ID | Read Only | Comments |
| --- | --- | --- |
| ISI\_PRIV\_LOGIN\_PAPI | True | Used to log in to the Platform API and the web administration interface. |
| ISI\_PRIV\_AUTH | True | Used to configure external authentication providers, including root-level accounts. |
| ISI\_PRIV\_DEVICES | True | Used to create new roles and assign privileges. |
| ISI\_PRIV\_JOB\_ENGINE R/W | False | Used for array Change File Tracking report scheduling for changelist API call. |
| ISI\_PRIV\_NETWORK | True | Used to configure network interfaces. |
| ISI\_PRIV\_NFS R/W | False | Used to update export rules. |
| ISI\_PRIV\_SMB | True | Used to configure the SMB server. |
| ISI\_PRIV\_SNAPSHOT R/W | False | Used to schedule, take, and view snapshots. |

For more information on privileges, see the [Dell documentation](https://www.dell.com/support/manuals/en-us/isilon-onefs/ifs_pub_administration_guide_cli/privileges?guid=guid-3c84bcda-2fff-4891-b14c-f1fe44f9c73b&lang=en-us).

You can use the following command to check privileges added to the VeeamStorageIntegration role:

|  |
| --- |
| isi auth roles view VeeamStorageIntegration |

Make sure that you make the service account to be used for NAS integration a member of the VeeamStorageIntegration role.

* To enable backup and restore of SMB file shares, additionally do the following:

* Grant minimum read access to SMB file shares for the account that will be used for NAS integration. That will allow backing up SMB file shares.
* Grant "run as root" access to SMB file shares for the account that will be used for NAS integration. That will allow restoring SMB file shares.

Consider that the PowerScale [BackupAdmin](https://www.dell.com/support/manuals/en-us/isilon-onefs/ifs_pub_administration_guide_cli/backupadmin-integrated-role?guid=guid-c17e3e17-e94e-4a03-8fbf-ef9ddcbe2521&lang=en-us) role is not enough for backup and restore. It is mainly used for SMB access and enables backup and restore of files from /ifs. It does not propagate down to subfolders and therefore cannot be used to backup anything, but the system access zone.

* To correctly use SmartConnect for NAS backup, consider the following:

1. Enable SmartConnect on the storage system as described in the Configuring SmartConnect section in the [Dell documentation](https://infohub.delltechnologies.com/nl-nl/l/configuration-best-practices-dell-emc-storage-with-s-1-video-management-software-svms/configuring-smartconnect-14/).
2. Configure DNS and DNS delegation as described in the Set up DNS for SmartConnect section in the [Dell documentation](https://infohub.delltechnologies.com/en-us/l/dell-emc-smartfabric-services-with-poweredge-servers-powerstore-storage-appliance-and-isilon-storage/set-up-dns-for-smartconnect-14/).
3. Add the storage system to the backup server as described in [Adding Dell PowerScale](dell_powerscale_add.md).
4. [Add general-purpose backup proxies](backup_proxy_general.md) to the backup infrastructure. We recommend adding as many general-purpose backup proxies as many Dell Powerscale storage nodes you plan to use for backup.

Dell PowerScale SmartConnect helps distribute the load among storage nodes: SmartConnect provides clients different IP addresses from different nodes to work with the storage cluster in parallel. If you do not use SmartConnect, Veeam Backup & Replication will use single IP address during backup, which can cause significant delays.


