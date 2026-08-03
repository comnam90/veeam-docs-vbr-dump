---
title: "Managing Worker Instances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_workers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Worker Instances


To perform most data protection and disaster recovery operations (such as creating and removing EC2 and RDS image-level backups, restoring backed-up data, EFS indexing), backup appliances use worker instances. Worker instances are temporary Linux-based EC2 instances that are responsible for the interaction between backup appliances and other solution architecture components. Worker instances process backup workload and distribute backup traffic when transferring data to backup repositories.

Each worker instance is deployed in a specific AWS Region for the duration of the backup, restore and retention process. AWS Regions in which backup appliances deploy worker instances to perform operations are predefined and described in section [Worker Instance Locations](aws_workers_location.md). However you can choose whether you want backup appliances to deploy worker instances in the backup account or in production AWS accounts, specify network settings and instance types that will be used to deploy worker instances. For more information on AWS accounts in which backup appliances deploy worker instances, see [Worker Deployment Options](aws_worker_options.md).

|  |
| --- |
| Note |
| You can tell worker instances from other EC2 instances running in your environment by their names — all worker instances deployed by backup appliances to perform backup and restore operations have the same name — VBA\_Worker, all worker instances deployed by backup appliances to perform EFS indexing have the same name — EFS\_Worker. |

In This Section

* [Managing Worker Configurations](aws_worker_settings.md)
* [Managing Worker Profiles](aws_worker_profiles.md)
* [Adding Worker Tags](aws_worker_tags.md)

Page updated 2026-07-15

