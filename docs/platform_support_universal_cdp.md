---
title: "Universal CDP"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_universal_cdp.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Universal CDP


A workload that you plan to protect with Universal CDP must meet the following requirements.

Microsoft Windows-Based

Microsoft Windows-Based

| Specification | Requirement |
| Hardware | CPU: x64.  Memory: 2 GB RAM or more. Memory consumption varies depending on the number and size of processed disks.  System firmware for Microsoft Windows: BIOS or UEFI.  Disk layout: GPT. |
| OS | 64-bit versions of the following operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 |
| File System | RAW, FAT, FAT32, exFAT, NTFS and ReFS |

Linux-Based

Linux-Based

| Specification | Requirement |
| Hardware | CPU: x64.  Memory: 2 GB RAM or more. Memory consumption varies depending on the number and size of processed disks.  System firmware for Linux: UEFI.  Disk layout: GPT. |
| OS | Linux kernel version starting from 5.10 is supported.  64-bit versions of the following Linux distributions are supported:   * RHEL 9.4–9.7 and 10.0-10.2 (Veeam CDP Volume Filter Driver installed from binary pre-build package)  * Rocky Linux 9.4–9.7 and 10.0-10.2 (Veeam CDP Volume Filter Driver installed from binary pre-build package)  * Alma Linux 9.4–9.7 and 10.0-10.2 (Veeam CDP Volume Filter Driver installed from binary pre-build package)  * Ubuntu 22.04 LTS, 24.04 LTS and 26.04 LTS (Veeam CDP Volume Filter Driver installed from dkms package)   For Debian, openSUSE, Oracle Linux, and other Linux-based OSes support is experimental. |
| File System | XFS, ext2, ext3, ext4, FAT16 and FAT32 |
| Software | Protected computer must have the following components installed:   * libudev (for managing devices during CDP) * libblkid (for managing devices during CDP)  * lvm2 (for LVM-related operations) * python3 (for installing Veeam CDP)\*   \* The python3 package or another RPM package providing a /usr/bin/python3 binary is required for RHEL 9.4 and later distributions if a pre-built binary veeamcdp kernel module package is to be installed.  The following components are required only for filter driver installed from dkms packages:   * kernel-headers (for RHEL-based systems) * kernel-devel (for RHEL-based systems) * linux-headers (for Debian-based systems) * linux-headers-amd64 (for Debian 13) * kernel-uek-devel (for Oracle Linux systems with UEK) * dkms * gcc * make * perl   Consider the following:   * To ensure proper functioning of the veeamcdp kernel module, verify that your system does not have any of the following modules installed: hcpdriver, snapapi26, snapapi, snapper, dattobd, dattobd-dkms, dkms-dattobd, cdr or cxbf. * [For Debian 13] Universal CDP installs the latest version of linux-headers-amd64 with the matching kernel and its headers. This can cause the kernel to be upgraded, which might affect drivers or software that rely on a specific kernel version. After kernel upgrade, you may need to rebuild or reinstall any custom kernel modules that you have on the system. * Version of the following packages varies according to the Linux kernel version that you use:  * linux-headers and linux-headers-amd64 (for Debian-based systems) * kernel-headers (for RedHat-based systems) * kernel-devel (for RedHat-based systems) * kernel-uek-devel (for Oracle Linux systems with UEK) |

For the full list of limitations and considerations, see [Universal CDP - Considerations and Limitations](uni_cdp_considerations.md).

Page updated 2026-06-23

