---
title: "Tape Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_tape_server.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Tape Server


Tape Server

| Specification | Requirement |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum. Using multi-core processors improves data processing performance and allows for more tasks to be processed concurrently.  Memory: 2 GB RAM plus 500MB for each concurrent task. Depending on the source of tape jobs, different entities are considered tasks: for machine backup to tape, a task covers a source job or a source chain if tape paralleling is enabled; for file backup to tape, a task covers an entire server or a file share. Restoring VMs directly from tape requires 400MB of RAM per 1TB of the restored virtual disk size. Tape cloning requires 1GB RAM for each concurrent task.  Disk Space: 300 MB, plus 10 GB for temporary data storage for backup and restore operations.  Network: 1 Gbps or faster.  For system requirements for backup to tape jobs, see the [Before You Begin](tape_before_you_begin.md#requirements) section for backup to tape.  For system requirements for large number of files in the file backup to tape job, see the [Before You Begin](file_to_tape_before_you_begin.md#many_files) section for file backup to tape. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported1:   * Debian 11.0 to 13.0 * Oracle Linux 7 (UEK3) to 10 (UEK R7) * Oracle Linux 7 to 10 (RHCK) * RHEL 8.6 to 10.0 * Rocky Linux 9.4 to 10.0 * SLES 12 SP5, 15 SP3 or later * Ubuntu: 20.04 LTS, 22.04 LTS, 24.04 LTS   1 Note that the tape server requires root access rights. For this reason, Veeam Software Appliance, [Veeam Infrastructure Appliance](linux_infrastructure_appliance_install.md) and hardened repository cannot be used as the tape server. |

For more information, see the [Tape Servers](tape_servers.md) section.


