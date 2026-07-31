---
title: "Worker Instances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sizing_worker_instances.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Worker Instances


Each worker instance is deployed as an Ubuntu image, and the binaries are downloaded from the provisioning Azure storage account. Azure VM sizes of worker instances depend on the total size of virtual disks attached to the processed Azure VM, on the total size of the processed Azure SQL database, or on the total size of the processed Cosmos DB for PostgreSQL cluster or the processed Cosmos DB for MongoDB account.

If you want initial full backups to be processed quickly, it is recommended that you use a larger worker profile, and then change it to a smaller profile for incremental backup. You can change worker profile settings on a regional basis, so make sure that the Azure VM sizes of worker instance size is appropriate to process the largest workload within the required time. For more information on configuring worker profiles, see [Managing Worker Instances](azure_worker_profiles.md).

Worker Instances

| Worker Profile | Default Azure VM Size | Usage | Backup Speed |
| Small | F2s\_v2 | Backing up Azure VMs with disks smaller than 100 GB, Azure SQL databases whose total size is less than 1 GB, Cosmos DB for PostgreSQL clusters and Cosmos DB for MongoDB accounts whose total size is less than 22 GB (default) | 70-85 MBps |
| Medium | F4s\_v2 | Backing up Azure VMs with disks between 100 GB and 1 TB, Azure SQL databases whose total size is between 1 GB and 50 GB, Cosmos DB for PostgreSQL clusters and Cosmos DB for MongoDB accounts whose total size is between 22 GB and 112 GB (default) | 90-100 MBps |
| Large | F8s\_v2 | Backing up Azure VMs with disks over 1 TB, Azure SQL databases whose total size is more than 50 GB, Cosmos DB for PostgreSQL clusters and Cosmos DB for MongoDB accounts whose total size is more than 112 GB, also recommended for initial full backup (default) | 125-140 MBps |
| Archiving | E2\_v5 | Data tiering (default) | 85-110 MBps |

For more information on Azure VM pricing, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes).

Recommended Maximums

You can modify the default number of worker instances to reduce the amount of processing time, and choose profiles that will be used to launch worker instances in the selected regions to boost operational performance. For more information, see [Adding Worker Profiles](azure_worker_profile_selection.md).

|  |
| --- |
| Note |
| If you plan to perform operations that require more than 50 worker instances at a time, or if you want to use custom worker profiles for retention operations or for Cosmos DB backup and restore, open a [support case](azure_support_information.md). |

Recommended Maximums

| Purpose | Recommended Maximum Number of Worker Instances |
| Default appliance size | 50 |
| Medium appliance size | 250 |
| Large appliance size | 500 |
| Maximum per region per appliance | 1,000 |
| Azure ARM API reads (per tenant/user/hour)\* | 12,000 |
| Azure ARM API writes (per tenant/user/hour)\* | 1,200 |

\*For more information on the Azure Management API request limits and throttling, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/request-limits-and-throttling).

Related Topics

* [Managing Worker Profiles](azure_worker_profiles.md)
* [Solution Architecture](azure_architecture_overview.md)

Page updated 2025-12-09

