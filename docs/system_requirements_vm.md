---
title: "System Requirements (VMware vSphere)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_vm.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# System Requirements (VMware vSphere)


Make sure that servers that you plan to use as backup infrastructure components to protect your VMware vSphere virtual machines meet the listed system requirements.

|  |
| --- |
| Note |
| The information on this page lists only infrastructure components specific for the protection of VMware vSphere virtual machines. For the list of all Veeam components, refer to [System Requirements](system_requirements.md). |

VMware Backup Proxy

VMware backup proxies can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements_via.md) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

System Requirements (VMware vSphere))

| Specification | Requirement |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum, plus 1 core (vCPU) for each 2 additional concurrent tasks. Using faster processors improves data processing performance. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#proxy).  Memory: 2 GB RAM plus 1 GB for each concurrent task. The actual size of memory required may be larger and depends on the amount of data to back up, machine configuration, and job settings. Using faster memory improves data processing performance.  Disk Space: 750 MB for Microsoft Windows-based proxies; 400 MB for Linux-based proxies.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported. Note that bash shell and SSH are required.   * Debian 11.0 to 13 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 20.04 LTS, 22.04 LTS, 24.04 LTS |

For more information, see the [VMware Backup Proxies](backup_proxy.md) section.

CDP Proxy

The following table shows the minimum system requirements for a CDP proxy.

VMware Backup ProxyVMware Backup ProxyVMware backup proxies can be deployed using the Veeam JeOS image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the Veeam Backup & Replication server.NoteComponent hardware requirements must be added to the Veeam JeOS system requirements to ensure that the assigned role has sufficient CPU and RAM resources. In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.SpecificationRequirementHardwareCPU: x86-64 processor with 2 cores (vCPUs) minimum, plus 1 core (vCPU) for each 2 additional concurrent tasks. Using faster processors improves data processing performance. For more information, see Limitation of Concurrent Tasks.Memory: 2 GB RAM plus 1 GB for each concurrent task. The actual size of memory required may be larger and depends on the amount of data to back up, machine configuration, and job settings. Using faster memory improves data processing performance.Disk Space: 750 MB for Microsoft Windows-based proxies; 400 MB for Linux-based proxies.Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.OSSystem Requirements - Windows OS64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:Microsoft Windows Server 2025Microsoft Windows Server 2022Microsoft Windows Server 2019Microsoft Windows Server 2016Microsoft Windows 11 (versions 22H2 – 25H2)Microsoft Windows 10 (version 22H2)Microsoft Windows 10 LTS (version LTSC 2021)64-bit versions of the following Linux distributions are supported. Note that bash shell and SSH are required.Debian 11.0 to 13Oracle Linux 7 to 10RHEL 8.6 to 9.6Rocky Linux 9 latest supported minor release, see Rocky Linux Wiki Rocky Linux Release and Version GuideSLES 12 SP5 or later, 15 SP3 or laterUbuntu: 20.04 LTS, 22.04 LTS, 24.04 LTSFor more information, see the VMware Backup Proxies section.

| Specification | Requirement |
| Hardware | CPU : x86-64 processor with 4 cores (vCPUs) minimum. Using multi-core processors improves data processing performance and allows for more tasks to be processed concurrently. Enabling the encryption may cause the performance reduction: in this case, increase the vCPU count up to 2 times.  Memory: 8 GB RAM minimum. Using more memory allows for longer peak write I/O periods before a CDP policy switches to the disk-based write I/O cache. Using faster memory improves data processing performance.  Disk Space: 300 MB plus disk-based write I/O cache (non-persistent data, at least 50 GB recommended). Larger cache allows for longer network downtime periods before a CDP policy switches to the CBT mode.  Network: 100 Mbps or faster. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported. Note that bash shell and SSH are required.   * Debian 11.0 to 13 * Oracle Linux from 8.3 (UEK R6 U2) to 9 (UEK R7) * Oracle Linux 7 to 9 (RHCK) * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 20.04 LTS, 24.04.3 LTS |

For more information, see the [CDP Proxies](cdp_proxy.md) section.

Veeam CDP Source and Target Datastores

The following source and target datastores are supported for Veeam CDP:

* NFS on file storage
* VMFS on block storage
* VMFS on internal ESXi storage
* VSAN

VSAN is supported for all hyper-converged infrastructure (HCI) appliances.

* vVol

vVol is supported for the following vendors: NetApp, HPE Nimble, Pure Storage and HPE 3PAR. For the list of tested vendor product lines, see [this Veeam KB article](https://www.veeam.com/kb4225).

Support for HCI appliances is pending validation by Veeam. The documentation will be updated based on the testing results. For the updates, see [CDP Requirements and Limitations](cdp_requirements.md).

|  |
| --- |
| Note |
| Consider the following:   * Cisco HyperFlex 4.5 (2a) and later can be used as a source or target only with VMware vSphere 7.0 U2 and later. With the previous versions of VMware vSphere, Cisco HyperFlex is not supported. * vVol and VSAN of each vendor have limits for the number of storage objects. Once the limit is reached, CDP starts to fail because creation of new objects cannot be completed. To restore the CDP process, remove some objects from VSAN/vVol. * CDP performance depends on your datastore characteristics. For better performance, check that your target datastore is able to process the I/O workload produced on the source datastore. |


