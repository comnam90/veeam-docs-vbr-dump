---
title: "cloud_replication_limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_replication_limitations.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup & Replication has the following specifics and limitations for Veeam Cloud Connect Replication.

Snapshot-Based Replication

* Veeam Cloud Connect Replication does not support DHCP. To allow a VM replica on the cloud host to be accessible over the network after failover, a replicated VM must have a static IP address.
* Automatic network settings detection is supported for Microsoft Windows VMs only. For cloud replication of non-Windows VMs, a tenant should specify network mapping settings and public IP addressing rules manually.
* A tenant cannot specify Re-IP rules for VM replicas on the cloud host. At the process of the replication job configuration, if a tenant selects the Re-IP option and then selects the cloud host as a replication target, Veeam Backup & Replication will disable the Re-IP option.
* Pick datastore option is not supported for replication jobs targeted at the cloud host.
* A tenant can restore VM guest OS files from a VM replica on the cloud host only to a Microsoft Windows file system.
* [For Microsoft Hyper-V VMs] Cloud replication of Shielded VMs is not supported. Replicas of such VMs can run only on guarded Hyper-V hosts that have access to Host Guardian Service deployed on the tenant side.
* Replication of encrypted VMs to a cloud host is not supported.
* If the SP uses a vSAN datastore as a target storage for tenant VM replicas, Veeam Backup & Replication will display double quota usage.

Replication to VMware Cloud Director

Before you start using VMware Cloud Director in the Veeam Cloud Connect infrastructure, consider the following prerequisites and limitations for VMware Cloud Director support:

* Veeam Cloud Connect supports VMware Cloud Director versions 10.1 to 10.6.
* If you plan to add more than one VMware Cloud Director server to the Veeam Cloud Connect infrastructure, make sure that names of VMware Cloud Director organizations and organization user accounts are unique within all VMware Cloud Director servers. Configurations with multiple Cloud Director servers that have identical organization and organization user account names are not supported.

Continuous Data Protection (CDP)

To learn about prerequisites and limitations for CDP with Veeam Backup & Replication, see the [Considerations and Limitations](https://helpcenter.veeam.com/docs/vbr/userguide/cdp_requirements.html?ver=13) section in the Veeam Backup & Replication User Guide.

In addition, Veeam Backup & Replication has the following limitations for CDP in the Veeam Cloud Connect infrastructure.

* To use the CDP functionality in the Veeam Cloud Connect environment, both the SP and tenant must run Veeam Backup & Replication version 12 or later.

* For the CDP to VMware vSphere scenario: the minimum required ESXi version on the SP and tenant side is 6.5 Update 2.
* For the CDP to VMware Cloud Director scenario:

* On the SP side, the minimum required ESXi version is 7.0.
* On the tenant side, the minimum required ESXi version is 6.5 Update 2.
* You must not use the same vApp as a target for both a snapshot-based replication job and a CDP policy.
* Organization VDC must have a CDP-ready storage policy. If no such policy is configured, Veeam Backup & Replication will check whether the default storage policy may be used for CDP and create a CDP-ready policy based on this storage policy.

Consider that the Any storage policy is not supported for CDP. If Organization VDC has Any as its default storage policy, Veeam Backup & Replication will not automatically create a CDP-ready policy based on it. In this case, the SP must create a CDP-ready policy and add it to the Organization VDC manually.

If a CDP-ready policy exists in VMware vSphere, and it has the same settings as the Default VDC storage policy, Veeam Backup & Replication will import it to VMware Cloud Director and use it for CDP.

If the SP creates new storage policies, they must make sure to configure a replication provider as well as the tags they need. The provider name is veecdp. For details, see [VMware Docs](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.storage.doc/GUID-2F47BFF7-88C8-43D3-96EB-C0ABE38F8B23.html). After that, this policy can be used as a CDP replication target.

Keep in mind that Veeam Backup & Replication should not use the existing storage policies that are applied to any VMs because Veeam Backup & Replication installs I/O filters on all VMs on this policy. This includes VMs that are out-of-scope of CDP. This can cause problems when removing I/O filters.

* CDP replication of encrypted VMs is not supported.
* CDP replication to a target datastore under a VM Encryption Policy is supported.

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
