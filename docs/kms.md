---
title: "Key Management System Keys"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/kms.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Key Management System Keys

In this article

You can use Key Management System (KMS) keys for data encryption instead of [secret keys based on a password](encryption_hiw.md). KMS keys are based on an asymmetric key encryption algorithm. They are managed and rotated by an external KMS server and provide a higher level of security.

You can use KMS keys to encrypt backup files on the following encryption levels:

* Job-level encryption:

+ Backup and backup copy jobs
+ Veeam Agent backup jobs managed by Veeam Backup & Replication
+ Application backup policies managed by Veeam Backup & Replication
+ File backup jobs and object storage backup jobs
+ Transaction log backup and backup copy jobs
+ VeeamZIP jobs

For more information about job-level encryption, see [Job Encryption](encryption_job.md).

|  |
| --- |
| Note |
| If you use Veeam Cloud Connect repositories as a target backup storage, you can also use KMS keys for the following jobs:   * Backup and backup copy jobs * Veeam Agent backup jobs managed by Veeam Backup & Replication  * Transaction log backup copy jobs |

* Storage-level encryption:

+ Backup repositories that store backup files created by:

* Veeam Plug-In for Nutanix AHV
* Veeam Backup for OLVM and RHV
* Veeam Kasten for Kubernetes
* Veeam Plug-Ins for Enterprise Applications operating in the standalone mode

For more information about storage-level encryption for Veeam Backup & Replication additional solutions, see [Encrypting Standalone Application Backups in Backup Repositories](encrypting_backups.md).

+ Capacity tier repositories. For more information about storage-level encryption for capacity tier repositories, see [Encryption for Capacity Tier](encryption_for_capacity_tier.md).
+ Media pools and GFS media pools. For more information about storage-level encryption for tape devices, see [Tape Encryption](encryption_tape.md).
+ External repositories (decryption only).

|  |
| --- |
| Important |
| The following jobs and repositories do not support data encryption with KMS keys:   * Configuration backup jobs * Veeam Agent backup jobs managed by Veeam Agents * Backup repositories that store backup files created by Veeam Agents operating in the standalone mode |

In This Section

* [How KMS Works](kms_how_it_works.md)
* [Requirements and Limitations](kms_requirements.md)
* [KMS Certificates](kms_certificates.md)
* [Adding KMS Server](kms_add_server.md)
* [Using KMS Keys](kms_use_keys.md)

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
