---
title: "Licensing"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/licensing.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# Licensing

In this article

To work with Veeam Backup & Replication, you must obtain a license key and install it on the backup server. If you do not install the license key, the product will operate in the Veeam Backup & Replication Community (free) Edition. For more information, see [Veeam Backup & Replication Community Edition](https://www.veeam.com/virtual-machine-backup-solution-free.html).

|  |
| --- |
| Important |
| Veeam Software Appliance operating in the Veeam Backup & Replication Community Edition supports only [data recovery](data_recovery_all.md) features. |

Veeam licenses Veeam Backup & Replication in 3 ways: per instance, per capacity, per socket.

You can use instance and socket licenses together. For more information, see [Merging Licenses](license_merge.md).

|  |
| --- |
| Note |
| Veeam Backup & Replication consumes licenses only to back up data, restore does not require licenses. You can restore VMs and data no matter how many available licenses you have or how many VMs you are restoring. |

For specific details on Veeam Agents licensing, see the following resources:

* If you work with Veeam Agents operating in the managed mode, see the [Licensing Requirements](agents_licensing_requirements.md) section in Veeam Agent Backup.
* If you work with Veeam Agents operating in the standalone mode, see the user guide for the Veeam Agent depending on the operating system of the protected computer. For example, if you work with Veeam Agent for Microsoft Windows, see the [Managing License](https://helpcenter.veeam.com/docs/agentforwindows/userguide/license_vbr.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.

Socket Licensing

|  |
| --- |
| Important |
| Socket licensing is not available if you use a Veeam Software Appliance as a backup server. |

With the socket licensing model, Veeam Backup & Replication is licensed by the number of CPU sockets on protected hosts. For more information, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html).

A license is required for every occupied motherboard socket as reported by the hypervisor API.

License is required only for source hosts — hosts on which VMs that you back up or replicate reside. Target hosts (for replication and migration jobs) do not need to be licensed.

The socket license assignment happens automatically as soon as you start a backup or replication job for VMs on a specific source host. You can revoke licenses from licensed hosts and re-apply them to other objects if needed. For more information, see [Revoking License](revoke_servers.md).

|  |
| --- |
| Note |
| If you use a socket license that was obtained for an earlier version of Veeam Backup & Replication, Veeam Software adds up to 6 gift (built-in) instances free of charge to your license scope. You can use these instances to protect any type of supported workloads except VMware and Hyper-V VMs — they are covered by the licensed CPU sockets on virtualization hosts.  If the number of licensed sockets is less than 6, you can use the number of instances that equals the number of licensed sockets. For example, if the number of licensed sockets is 5, you can use 5 instances. If the number of licensed sockets is 100, you can use 6 instances.  Note that starting with Veeam Backup & Replication 12, the gift (built-in) instances are disabled if the perpetual license support expiration date is reached. |

Instance Licensing

Veeam Backup & Replication can be licensed by the number of instances. Instances are units (or tokens) that you can use to protect your virtual, physical or cloud-based workloads. For more information, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html).

You must obtain a license with the total number of instances for workloads that you plan to protect in Veeam Backup & Replication.

Workloads that have been processed in the past 31 days are considered protected. Every protected workload consumes instances from the license scope. The number of instances that a workload requires depends on the workload type and product edition.

This licensing model allows you to obtain a license with a certain number of instances without knowing in advance what types of workloads you plan to protect. When a need arises, you can revoke instances from a protected workload, and reuse them to protect other workloads regardless of the workload type.

Veeam Backup & Replication keeps track of instances consumed by protected workloads. If the number of consumed instances exceeds the license limit, Veeam Backup & Replication displays a warning when you open the Veeam Backup & Replication console. For more information, see [Exceeding License Limit](license_exceeding.md).

Consider the following:

* VM templates are regarded as protected VMs and consume license instances.

* VMs and unstructured data sources processed with backup copy and tape jobs are not regarded as protected VMs and data sources and do not consume license instances. These types of jobs provide an additional protection level for VMs and unstructured data sources that are already protected with backup jobs.

* [For VMware vSphere] VMs processed by snapshot-only jobs are regarded as protected VMs and consume license instances. Veeam Backup & Replication will revoke instances from these VMs if you re-add a storage array to the backup infrastructure.

* For more information on how Veeam Backup & Replication calculates license instances to consume when protecting unstructured data sources, see [Instance Consumption for Object Storage Backup, File Backup and File to Tape Jobs](nas_licensing.md).

Capacity Licensing

Veeam Backup & Replication can be licensed by the capacity of protected data. TBs of front-end storage capacity pack are units that you can use to protect your non-deduplicated and uncompressed front-end source data in unstructured data sources (file servers, file shares, NAS filers, object storage repositories). For more information, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html).

You must obtain a license with the total capacity for source data that you plan to protect in Veeam Backup & Replication.

Data sources that have been processed in the past 31 days are considered protected. Every protected data source consumes capacity from the license scope.

This licensing model allows you to obtain a license with a certain license capacity without knowing in advance what types of unstructured data sources you plan to protect. When a need arises, you can revoke license capacity from a protected data source, and reuse it to protect other data sources regardless of the workload type.

Veeam Backup & Replication keeps track of capacity consumed by protected data sources. If the number of consumed capacity licenses exceeds the license limit, Veeam Backup & Replication displays a warning when you open the Veeam Backup & Replication console. For more information, see [Exceeding License Limit](license_exceeding.md).

Consider the following:

* Veeam Backup & Replication rounds the protected amount of data for each unstructured data source down to 1 TB.

* Capacity license is consumed in 1 TB chunks.

* When your unstructured data sources are protected with file backup to tape or object storage backup to tape jobs, Veeam backup files are excluded from the capacity consumption calculation. These files have the following extensions: VAB, VBM, VBK, VIB, VRB, VSB, VLB, VSM, VLM, VOM, VACM, VASM, VSOURCE, VSOURCETEMP, VSTORE, VSTORETEMP, VSLICE, VBASKET, VLIST, VCACHE, VBLOB, BCO, ADB.

* If different data sources are protected with different file backup or object storage backup jobs or with different file backup to tape or object backup to tape jobs, Veeam Backup & Replication rounds the protected amount to 500 GB separately for each data source and calculates the number of instances required to protect each of them. After that, it sums up the total number of license instances to consume for unstructured data backup or for unstructured data backup to tape.

* If the same data source is protected with more than one unstructured data backup job, to calculate the size of the protected amount of data Veeam Backup & Replication first sums the size of the source data protected with all the jobs. After that, it rounds the overall protected amount of data down to 500 GB and calculates the license capacity to consume for the unstructured data backup.

* Unstructured data sources processed with backup copy and backup to tape jobs are not regarded as protected data sources and do not consume the license capacity. These types of jobs provide an additional protection level for unstructured data sources that are already protected with backup jobs.

* Veeam Backup & Replication calculates the protected amount of data for each data source during every run of the unstructured data backup job or unstructured data backup to tape job that protects data on this data source and keeps the result for 30 days. To calculate the license capacity to consume for the data source protection, Veeam Backup & Replication takes the largest protected amount of data on the data source within the last 30 days.

If the size of the protected data reduces and does not increase or the data source is removed from the unstructured data backup job or unstructured data backup to tape job, after 30 days Veeam Backup & Replication recalculates the protected amount of data and automatically revokes the excessively consumed license capacity. You can manually revoke the licenses without waiting for 30 days, as described in the [Revoking License](revoke_servers.md) section. During the next unstructured data backup job or unstructured data backup to tape job run, Veeam Backup & Replication will recalculate the license capacity consumption as of the current date.

* If an unstructured data backup job protects several file shares residing on the same NAS device (the same share root or NAS filer), the approach to calculating license consumption depends on how the file shares are added to the infrastructure:

* If you have added the whole share root (\\root\) to the infrastructure and the file backup job protects shares \\root\share1 and \\root\share2, Veeam Backup & Replication first sums the protected amount of both file shares, rounds it down to 500 GB, and then calculates the license consumption to consume for file backup support.
* If you have separately added shares \\root\share1 and \\root\share2 to the infrastructure and the file backup job protects both of them, Veeam Backup & Replication first rounds the protected amount for each file share down to 500 GB, separately calculates the license capacity to consume for each file share, and then sums the license capacity to calculate the total license capacity to consume for file backup support.

* Unstructured data backup to an object storage requires a license. Thus, this feature is not supported in the Veeam Backup & Replication Community (free) Edition. For details, see [Veeam Editions Comparison](https://www.veeam.com/backup-version-standard-enterprise-editions-comparison.html).
* Unstructured data restore from an object storage does not require a license. Thus, this feature is supported in the Veeam Backup & Replication Community (free) Edition. For details, see [Veeam Editions Comparison](https://www.veeam.com/backup-version-standard-enterprise-editions-comparison.html).

In This Section

* [Types of Licenses](types_of_licenses.md)
* [Instance Consumption for Object Storage Backup, File Backup and File to Tape Jobs](nas_licensing.md)
* [Obtaining and Renewing License](license_obtain.md)
* [Installing License](install_license.md)
* [Merging Licenses](license_merge.md)
* [Viewing License Information](license_view.md)
* [Revoking License](revoke_servers.md)
* [Removing License](removing_license.md)
* [Exceeding License Limit](license_exceeding.md)
* [License Expiration](license_grace.md)
* [Updating License](license_update.md)
* [Automatic License Usage Reporting](automatic_usage_logging.md)

Page updated 12/30/2025

Page content applies to build 13.0.1.1071
