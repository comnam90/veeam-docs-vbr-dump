---
title: "CDP Proxy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_cdp_proxy.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# CDP Proxy


The following table shows the minimum system requirements for a CDP proxy.

CDP Proxy

| Specification | Requirement |
| Hardware | CPU : x86-64 processor with 4 cores (vCPUs) minimum. Using multi-core processors improves data processing performance and allows for more tasks to be processed concurrently. Enabling the encryption may cause the performance reduction: in this case, increase the vCPU count up to 2 times.  Memory: 8 GB RAM minimum. Using more memory allows for longer peak write I/O periods before a CDP policy switches to the disk-based write I/O cache. Using faster memory improves data processing performance.  Disk Space: 300 MB plus disk-based write I/O cache (non-persistent data, at least 50 GB recommended). Larger cache allows for longer network downtime periods before a CDP policy switches to the CBT mode.  Network: 100 Mbps or faster. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported. Note that bash shell and SSH are required.   * Debian 11.0 to 13 * Oracle Linux from 8.3 (UEK R6 U2) to 9 (UEK R7) * Oracle Linux 7 to 9 (RHCK) * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 20.04 LTS, 24.04.3 LTS |

For more information, see the [CDP Proxies](cdp_proxy.md) section.


