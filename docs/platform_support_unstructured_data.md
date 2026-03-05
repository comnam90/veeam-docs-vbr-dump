---
title: "Unstructured Data"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_unstructured_data.html"
last_updated: "3/4/2026"
product_version: "13.0.1.1071"
---

# Unstructured Data


Veeam Backup & Replication supports protection of the following sources of unstructured data:

Unstructured Data

| Type | Data Source |
| Object Storage Repositories | The following object storage sources are supported:   * Amazon S3 object storage * Microsoft Azure Blob storage * Azure Data Lake Gen2 storage (HNS) * S3-compatible object storage |
| Files Servers | The following Microsoft Windows operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows 11 (versions 22H2, 23H2, 24H2) * Microsoft Windows 10 22H2 * Microsoft Windows 10 LTSC 2021   64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 12.11 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6 * Rocky Linux 9.4 to 9.6 * SLES 12 SP5, 15 SP3 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS |
| Enterprise NAS Systems | The following enterprise NAS systems are supported:   * NetApp FAS/AFF/ASA, FlexArray (V-Series), ONTAP Edge/Select/Cloud VSA with ONTAP cluster-mode versions from 9.10 up to 9.17.1 * Lenovo ThinkSystem DM/DG Series with ONTAP cluster-mode versions 9.10 to 9.17.1 * Fujitsu ETERNUS HX/AX with ONTAP cluster-mode versions 9.10 to 9.17.1 * Dell PowerScale (formerly Isilon) with OneFS versions 8.1.2 to 9.11 * Nutanix Files Storage versions 3.8.1.3 to 5.2 |
| File Shares | The following file share sources are supported:   * SMB version 1.x, 2.x or 3.x. * NFS protocol version 3 or 4.1. |

Requirements and Limitations for File Shares

Consider the following requirements and limitations for file shares:

* Only 64-bit versions of operating systems are supported for managed Microsoft Windows or Linux server file share.
* Backup of file shares on Linux hosts [added with single use credentials](hardened_repository.md) is not supported.
* NFS file share must run NFS protocol version 3 or 4.1. Parallel NFS (pNFS) is not supported.
* Network shares and files on them targeted to 3rd party storage devices may have difficulties being restored, or may not be restored at all. Such shares/files often rely upon specific software/OS filters to be recalled from the alternate storage location, which is not available when performing a file share data recovery. See your software vendor documentation to learn how to back up such files.
* Anonymous or AD/Kerberos authentication is not supported for access to file shares through NFS.

In NFS settings of the source file share, you must explicitly specify what servers will have access to the file share.

* SMB file share must run on SMB version 1.x, 2.x or 3.x.
* To support the VSS for SMB File Shares feature, make sure that requirements listed in [this Veeam KB article](https://www.veeam.com/kb3099) are met.
* To correctly back up SACL (Ownership) files and folders from the SMB file share and restore them:

1. When you are [specifying access settings for the SMB file share](file_share_backup_smb_share_path_credentials.md), select the This share requires access credentials check box.
2. Make sure that the account you use to [Unstructured Data Backup](unstructured_data_backup.md) access the file share is either added to the Backup Operators group or has the SeBackupPrivilege and SeRestorePrivilege privileges in Windows Server on the file share.


