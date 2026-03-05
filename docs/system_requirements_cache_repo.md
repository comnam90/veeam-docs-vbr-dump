---
title: "Cache Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_cache_repo.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Cache Repository


The following storage types can be used as a cache repository for unstructured data backup:

* Direct attached storage. You can add virtual and physical servers as cache repositories:

* [Microsoft Windows server](ms_server.md) (only 64-bit versions are supported).
* [Linux server](linux_server.md) (only 64-bit versions are supported).

* Network attached storage. You can add [SMB (CIFS) Share](smb_share.md) or [NFS Share](nfs_share.md) as a cache repository.

Cache Repository

| Specification | Requirement |
| Hardware | Cache repository hardware requirements depend on the target backup repository.  For direct attached storage, network attached storage (NAS) or deduplicating storage appliance as the backup target:   * CPU: x86-64 processor with 2 cores (vCPUs), plus 4 cores (vCPUs) for each concurrently processed unstructured data source.  * Memory: 4 GB RAM, plus 4 GB RAM for each concurrently processed unstructured data source.  * Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.   For object storage as the backup target:   * CPU: x86-64 processor with 2 cores (vCPUs), plus 6 cores (vCPUs) for each concurrently processed unstructured data source. * Memory: 4 GB RAM, plus 16 GB RAM for each concurrently processed unstructured data source. * Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 12.11 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 or later * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Bash shell and SSH are required to deploy the management agent (SSH connection is not required for updating Veeam components and can be disabled afterwards). Perl is required only for [non-persistent Veeam Data Movers](veeam_transport_service.md). Check the full list of required Perl modules in [this Veeam KB article](https://www.veeam.com/kb2216).  For advanced XFS integration (fast clone), only the following 64-bit Linux distributions are supported:   * Debian 11.0 to 12.11  * RHEL 8.6 to 9.6  * Rocky Linux 9.4 to 9.6  * SLES 15 SP3 or later * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   For other distributions, XFS integration support is experimental, with kernel version 5.4 or later recommended. For more information, see [this Veeam KB article](https://www.veeam.com/kb2976). |

For more information, see Cache Repository in the [Backup Infrastructure for Unstructured Data Backup](unstructured_data_backup_infrastructure.md) section.

Cache Repository for Object Storage Repository

If the cache repository works with an unstructured data source being backed up to an object storage repository, it also processes active metadata that is heavily used during backup and restore operations. So you will require more disk space for the cache repository. The volume of this disk space depends on the number of the file versions on the data source and the number of unstructured data backup jobs that protect this data source. We recommend allocating not less than 1 GB of disk space for active metadata of each 1,000,000 file versions protected with 1 file backup job or object storage backup job. If you protect the same data source, for example, with 2 different backup jobs, the volume of metadata will double. For more information, see the [Unstructured Data Backups in Object Storage Repositories](unstructured_data_backup_in_object_storage.md) section.

|  |
| --- |
| Tip |
| We strongly recommend utilizing a fast storage disk, for example, an SSD in the role of the cache repository used for working with an object storage repository. |


