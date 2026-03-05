---
title: "Oracle Solaris Computers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_agent_management_solaris.html"
last_updated: "2/25/2026"
product_version: "13.0.1.1071"
---

# Oracle Solaris Computers


A computer that you want to protect with Veeam Agent for Oracle Solaris must meet the following requirements:

Oracle Solaris Computers

| Specification | Requirement |
| Hardware | CPU: Oracle SPARC or Intel x86 processor.  Memory: 1 GB RAM (for standard backup and restore operations) / 4 GB RAM (for bare metal recovery).  Disk space: 250 MB free disk space for product installation.  Network: 10 Mbps or faster network connection to a backup target. |
| OS | Oracle Solaris 10 1/13, 11.3 and 11.4 operating systems on machines based on the SPARC or Intel x86 architecture are supported.  Note: Only GA versions of the Oracle Solaris OS that have been released before the Veeam Agent for Oracle Solaris version 13.0.1 are supported. |
| File System | All file systems supported by the supported operating systems.  Consider the following:   * Total size of all file systems included in a file-level backup must not exceed 216 TiB. * Size of a file in a backup must not exceed 16 TiB. * Name of a file in a backup must not be larger than 254 bytes.   Keep in mind that characters that you can use in the file name may be encoded in 2 bytes or more.   * Sparse files are not supported. Veeam Agent backs up and restores sparse files as regular files. * Backup of clustered systems is not supported. * Veeam Agent supports backup and restore of POSIX and NFSv4 Access Control Lists (ACLs). For more information, see [Backup of ACLs](agents_backup_unix_acl.md). |
| Software | IMPORTANT! The user account used to work with Veeam Agent for Oracle Solaris installed on the protected computer must have the /bin/bash shell set as the default shell.  For file system indexing, the following utilities are required: tar, mlocate and gzip.   * mlocate (version 0.26-1 or later) – required for file system indexing. If your system does not have the mlocate utility, you can install it from the product installation media. * tar - required for file system indexing, exporting and rotating logs. It is installed with the product. * gzip – required for file system indexing, exporting and rotating logs. It must be installed separately. * xorriso – required for creating Veeam Recovery Media.   Oracle Solaris minimal install (Core System Support Software Group) requires adding the following packages: SUNWtoo, SUNWzoneu and SUNWzoner.  If you use Veeam Backup & Replication on Linux, OpenSSH is required for Veeam Agent installation. On Oracle Solaris 10 1/13 and 11.3, OpenSSH must be installed manually. For more information, see [this Veeam KB article](https://www.veeam.com/kb4735). |


