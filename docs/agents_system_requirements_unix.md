---
title: "System Requirements for Unix Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_system_requirements_unix.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# System Requirements for Unix Computers

In this article

This topic lists system requirements for Veeam Agent computers that run on [IBM AIX](#aix) or [Oracle Solaris](#sol).

Veeam Agent Computer (IBM AIX)

A computer that you want to protect with Veeam Agent for IBM AIX must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| Hardware | Memory: 1 GB RAM (for standard backup and restore operations) / 4 GB RAM (for bare metal recovery).  Disk space: 1.5 GB free disk space for product installation.  Network: 10 Mbps or faster network connection to a backup target. |
| OS | IBM AIX 7.1 – 7.3 TL3 are supported.  Note:  * Only GA versions of the IBM AIX operating system that have been released before the Veeam Agent for IBM AIX 13.0.1 are are supported. * Backup of a Virtual I/O Server (VIOS) is not supported. |
| File System | All file systems supported by the supported operating systems.  Consider the following:   * Total size of all file systems included in a file-level backup must not exceed 216 TiB. * Size of a file in a backup must not exceed 16 TiB. * Name of a file in a backup must not be larger than 254 bytes.   Keep in mind that characters that you can use in the file name may be encoded in 2 bytes or more.   * Sparse files are not supported. Veeam Agent backs up and restores sparse files as regular files. * JFS2 snapshots are not supported.  * Backup of clustered systems (including IBM PowerHA SystemMirror) is not supported.  * Veeam Agent supports backup and restore of NFSv4 Access Control Lists (ACLs). For more information, see [Backup of ACLs](agents_backup_unix_acl.md). |
| Software | IMPORTANT! The user account used to work with Veeam Agent for IBM AIX installed on the protected computer must have the /bin/bash shell set as the default shell.  The following utilities must be installed on the machine:   * mlocate — required for file system indexing. You must use the mlocate utility that is provided with Veeam Agent in the product installation media.   If you upgrade to Veeam Agent for IBM AIX version 12.1 and you have the mlocate utility provided with one of the previous versions of Veeam Agent for IBM AIX installed in your system, you must replace the existing mlocate utility with the mlocate utility provided with Veeam Agent in the product installation media.   * tar — required for file system indexing, exporting and rotating logs. It is installed with the product. * gzip — required for file system indexing, exporting and rotating logs. It must be installed separately. * mkisofs — required for creating Veeam recovery Media.   [For IBM AIX 7.3, 7.2 and 7.1 TL1 or higher] This utility is pre-installed in the OS and does not require separate installation.  [For IBM AIX 7.1 TL0] You must install version 1.13 of the mkisofs utility.   * [For IBM AIX 7.1] bos.rte.libc version 7.1.5.0 or later must be installed. |

AIX Environment

The LIBPATH AIX environment variable on the Veeam Agent computer must be set to blank (default value). If a different value is specified for this variable, you must make adjustments to the AIX environment for proper operation of Veeam Agent. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4273).

Veeam Agent Computer (Oracle Solaris)

A computer that you want to protect with Veeam Agent for Oracle Solaris must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: Oracle SPARC or Intel x86 processor.  Memory: 1 GB RAM (for standard backup and restore operations) / 4 GB RAM (for bare metal recovery).  Disk space: 250 MB free disk space for product installation.  Network: 10 Mbps or faster network connection to a backup target. |
| OS | Oracle Solaris 10 1/13, 11.3 and 11.4 operating systems on machines based on the SPARC or Intel x86 architecture are supported.  Note: Only GA versions of the Oracle Solaris OS that have been released before the Veeam Agent for Oracle Solaris version 13.0.1 are supported. |
| File System | All file systems supported by the supported operating systems.  Consider the following:   * Total size of all file systems included in a file-level backup must not exceed 216 TiB. * Size of a file in a backup must not exceed 16 TiB. * Name of a file in a backup must not be larger than 254 bytes.   Keep in mind that characters that you can use in the file name may be encoded in 2 bytes or more.   * Sparse files are not supported. Veeam Agent backs up and restores sparse files as regular files. * Backup of clustered systems is not supported. * Veeam Agent supports backup and restore of POSIX and NFSv4 Access Control Lists (ACLs). For more information, see [Backup of ACLs](agents_backup_unix_acl.md). |
| Software | IMPORTANT! The user account used to work with Veeam Agent for Oracle Solaris installed on the protected computer must have the /bin/bash shell set as the default shell.  For file system indexing, the following utilities are required: tar, mlocate and gzip.   * mlocate (version 0.26-1 or later) – required for file system indexing. If your system does not have the mlocate utility, you can install it from the product installation media. * tar - required for file system indexing, exporting and rotating logs. It is installed with the product. * gzip – required for file system indexing, exporting and rotating logs. It must be installed separately. * xorriso – required for creating Veeam Recovery Media.   Oracle Solaris minimal install (Core System Support Software Group) requires adding the following packages: SUMWtoo, SUNWzoneu and SUNWzoner.  If you use Veeam Backup & Replication on Linux, OpenSSH is required for Veeam Agent installation. On Oracle Solaris 10 1/13 and 11.3, OpenSSH must be installed manually. For more information, see [this Veeam KB article](https://www.veeam.com/kb4735). |

Page updated 11/6/2025

Page content applies to build 13.0.1.1071
