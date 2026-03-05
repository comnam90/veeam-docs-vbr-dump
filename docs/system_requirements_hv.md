---
title: "System Requirements (Microsoft Hyper-V)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_hv.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# System Requirements (Microsoft Hyper-V)


Make sure that servers that you plan to use as backup infrastructure components to protect your Microsoft Hyper-V virtual machines meet the listed system requirements.

|  |
| --- |
| Note |
| The information on this page lists only infrastructure components specific for the protection of Microsoft Hyper-V virtual machines. For the list of all Veeam components, refer to [System Requirements](system_requirements.md). |

Limitations and Recommendations

Native Hyper-V Replication

Do not use native Hyper-V replication especially if replication is targeted at the same scope (host, cluster, SCVMM) where the source VM resides. This can cause VM ID collision. Instead, we recommend you use Veeam replication. For more information, see [Replication](replication.md).

Hyper-V Off-Host Backup Proxy or Hyper-V Host as Backup Proxy

You can deploy and manage backup proxies on supported operating systems of your choice.

Native Hyper-V Replication

| Specification | Requirement |
| Hardware | CPU: modern x86-64 processor with 2 cores (vCPUs) minimum. It is recommended to add 1 core (vCPU) for each 2 additional concurrent tasks. Using faster processors improves data processing performance. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#proxy).  Memory: 2 GB RAM plus 500 MB for each concurrent task. The actual size of memory required may be larger and depends on the amount of data to back up, machine configuration, and job settings. Using faster memory improves data processing performance.  Disk Space: 300 MB.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 |
| Software | For off-host backup from CSV (SAN): VSS hardware provider that supports transportable shadow copies. The VSS hardware provider is typically distributed as a part of client components supplied by the storage vendor.  Not required for off-host backup from SMB shared storage. |

For more information, see the [Off-Host Backup Proxies](offhost_backup_proxy.md) section.

If you use the on-host backup mode, note that the source Hyper-V host performing the role of the backup proxy will require additional computing resources similar to those specified as the off-host backup proxy requirements. For more information, see [On-Host Backup](onhost_backup.md).


