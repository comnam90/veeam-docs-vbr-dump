---
title: "Managing Worker Profiles"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_worker_profiles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Worker Profiles


Worker profiles are instance types of worker instances that backup appliances deploy in a specific AWS Region to perform backup, restore, archive and health check operations. Backup appliances deploy one worker instance per each AWS resource added to a backup policy or restore task. The profile of each deployed worker instance is selected based on the performed operation and the size of EBS volumes attached to the processed instance.

There are 4 types of worker profiles in backup appliances:

* Small profile — a profile that is used for backup and restore operations if the total size of all EBS volumes of the processed instance is less than 1024 GB (for EC2 instances) and is less than 80 GB (for RDS resources).
* Medium profile — a profile that is used for backup and restore operations if the total size of all EBS volumes of the processed instance is 1024 GB–16 TB (for EC2 instances) and more than 80 GB (for RDS resources).
* Large profile — a profile that is used for backup and restore operations if the total size of all EBS volumes of the processed instance is more than 16 TB (for EC2 instances).
* Archiving profile — a profile that is used for creating EC2 and RDS archives.

Out of the box, backup appliances come with the default set of worker profiles where the small profile for both EC2 instances and RDS resources is c5.large, the medium profile for EC2 instances is c5.2xlarge, the medium profile for RDS resources is c5.xlarge, the large profile for EC2 instances is c5.4xlarge, the archiving profile for both EC2 instances and RDS resources is c5.2xlarge. However, to boost operational performance, you can add custom sets of worker profiles to specify instance types of worker instances that will be deployed in different regions.

|  |
| --- |
| Important |
| You cannot change the default worker profile used to deploy worker instances that perform EC2 file-level recovery, EFS indexing and retention operations — the default instance sizes of the these worker instances are described in section [Worker Instance Locations](aws_workers_location.md). If you want to use a specific instance size for these worker instances, open a [support case](aws_logs.md). |

In This Section

* [Adding Profiles](aws_worker_add_profile.md)
* [Editing Profiles](aws_worker_edit_profile.md)
* [Removing Profiles](aws_worker_remove_profile.md)

Page updated 2026-07-23

