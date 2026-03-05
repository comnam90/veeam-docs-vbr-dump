---
title: "Linux Helper Host"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_linux_helper_host.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Linux Helper Host


Linux helper hosts can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements_via.md) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

|  |
| --- |
| Note |
| Bash shell and SSH are required. |

Linux Helper Host

| OS | Version/Distribution |
| Linux | 64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 13.1 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Note: If you use RHEL or Rocky Linux version 9 or later, do not use [Veeam Infrastructure Appliance](linux_infrastructure.md), and mount disks with the NTFS file system, you must install the ntfs-3g package before adding the server to the backup infrastructure. |
| IBM AIX | The following versions of the operating system are supported:  IBM AIX 7.1 – 7.3 TL2 |
| Oracle Solaris | The following versions of the operating system are supported:  Oracle Solaris 10 1/13, 11.0 – 11.4 |

For more information, see [Guest OS File Restore](guest_file_recovery.md).


