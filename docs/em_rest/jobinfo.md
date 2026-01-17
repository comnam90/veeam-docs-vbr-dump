---
title: "Job Info"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/jobinfo.html"
last_updated: "8/14/2025"
product_version: "13.0.1.1071"
---


In this article

The JobInfo element of the job resource includes one of the following complex elements depending on the job type.

| Element | Type | Description |
| --- | --- | --- |
| BackupJobInfo | BackupJobInfoType | Backup job settings. For details, see [Backup Job](#BackupJob). |
| ReplicaJobInfo | ReplicaJobInfoType | Replication job settings. For details, see [Replication Job](#ReplicationJob). |
| BackupCopyJobInfo | BackupCopyJobInfoType | Settings of periodic backup copy jobs created by Veeam Backup & Replication 11a or earlier versions. For details, see [Periodic Backup Copy Job](#ReplicationJob). |
| ImmediateBackupCopyJobInfo | ImmediateBackupCopyJobInfoType | Settings of all immediate backup copy jobs as well as periodic backup copy jobs created by Veeam Backup & Replication 12. For details, see [Immediate Backup Copy Job](#ImmediateBackupCopyJob). |

Backup Jobs

The BackupJobInfo element of backup jobs contains the following elements.

| Element | Type | Description |
| --- | --- | --- |
| Includes | ObjectInJobListType | Collection of VMs and VM containers processed by the job. For details, see [GET /jobs/{ID}/includes/{ID}](get_jobs_id_includes_id.md#response_body). |
| GuestProcessingOptions | GuestProcessingOptionsType | Options for application-aware image processing. For details, see [Guest Processing Options](guestprocessingoptions.md). |
| AdvancedStorageOptions | AdvancedStorageOptionsType | Advanced storage options that contain a password key ID. |
| GfsRetentionPolicy | GfsRetentionPolicyOptionsInfoType | Long-term (GFS) retention policy settings. For details, see [Simple and GFS Retention Policies](simple_and_gfs_retention_policies.md). |
| SimpleRetentionPolicy | SimpleRetentionPolicyInfoType | Short-term retention policy settings. For details, see [Simple and GFS Retention Policies](simple_and_gfs_retention_policies.md). |

Replication Jobs

The ReplicaJobInfo element of replication jobs contains the following elements.

| Element | Type | Description |
| --- | --- | --- |
| Includes | ObjectInJobListType | Collection of VMs and VM containers processed by the job. For details, see [GET /jobs/{ID}/includes/{ID}](get_jobs_id_includes_id.md#response_body). |
| GuestProcessingOptions | GuestProcessingOptionsType | Options for application-aware image processing. For details, see [Guest Processing Options](guestprocessingoptions.md). |

Backup Copy Jobs

The settings of immediate backup copy jobs as well as periodic backup copy jobs created with Veeam Backup & Replication 12 or later are represented by the ImmediateBackupCopyJobInfo element. ImmediateBackupCopyJobInfo contains the following elements.

| Element | Type | Description |
| --- | --- | --- |
| LinkedJobIncludes | LinkedJobListType | Collection of linked backup jobs. For details, see [Backup Copy Job Options](backup_copy_job_options.md). |
| LinkedBackupIncludes | LinkedBackupIncludes | Collection of linked backups. For details, see [Backup Copy Job Options](backup_copy_job_options.md). |
| LinkedBackupRepositoryIncludes | LinkedBackupRepositoryIncludes | Collection of linked backup repositories. For details, see [Backup Copy Job Options](backup_copy_job_options.md). |

The settings of periodic backup copy jobs created with Veeam Backup & Replication 11a or earlier versions are represented by the BackupCopyJobInfo element. BackupCopyJobInfo contains the following elements.

| Element | Type | Description |
| --- | --- | --- |
| Includes | ObjectInJobListType | Collection of VMs and VM containers processed by the job. For details, see [GET /jobs/{ID}/includes/{ID}](get_jobs_id_includes_id.md#response_body). |
| LinkedJobIncludes | LinkedJobListType | Collection of linked backup jobs. For details, see [Backup Copy Job Options](backup_copy_job_options.md). |
| AdvancedStorageOptions | AdvancedStorageOptionsType | Advanced storage options that contain a password key ID. |
| LinkedBackupIncludes | LinkedBackupListType | Collection of linked backups. For details, see [Backup Copy Job Options](backup_copy_job_options.md). |

Page updated 8/14/2025

Page content applies to build 13.0.1.1071
