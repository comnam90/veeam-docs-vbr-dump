---
title: "Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sizing_backup_policies.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Backup Policies


Since one policy can be used to protect multiple workloads at the same time, it is recommended that you limit the number of processed workloads to simplify the backup schedule and to optimize the backup performance.

General Recommendations

This section provides best practices for the maximum number of workloads per policy. This number does not depend on the Azure VM size of the backup appliance.

General Recommendations

| Resource | Maximum Workloads per Policy |
| Azure VM | 500 |
| Azure SQL database | 200 |

In Microsoft Azure, there is an [ingress limit](https://learn.microsoft.com/en-us/azure/storage/common/scalability-targets-standard-account) for Azure storage accounts, which is 7.5 GBps or approximately 60 Gbps. With 50 workloads per repository, the expected writing speed to the target backup repository is approximately 7.3 GBps (engaging 50 worker instances of the F8s\_v2 Azure VM size), which falls under the limit. It is possible to protect more than 50 workloads per policy; however, you must configure the load options for the target backup repository as described in section [Adding Backup Repositories](azure_repository_ui_load.md) or [Adding Storage Vaults](azure_repository_vdc_ui_load.md).

|  |
| --- |
| Note |
| The performance of backup operations depends on the total volume of the processed workload data and on the size of incremental backups. That is why you need to make sure that your backup appliance has enough time to successfully run both backup and retention sessions. |

Maximizing Throughput

The number of worker instances simultaneously launched to process workloads added to a policy is defined by the speed of data upload to the repository specified for the policy. To maximize policy processing throughput, take into account that every backup and archive session started during policy execution requires a separate worker instance to be launched. For more information, see [Worker Instances](azure_sizing_worker_instances.md).

For example, one backup policy can only write to one storage account. When using a F2s\_v2 worker size with 80 MBps throughput to a storage account that can handle 25 Gbps, you can have a maximum of 3 GBps of throughput to the storage account, so a maximum of 38 worker instances. This means that for a policy that protects approximately 50 workloads, the recommended maximum number of worker instances processing simultaneously is 38.

Maximizing Throughput

| Workloads in Policy | Recommended Maximum Number of Worker Instances | Worker Instance Size | Worker Instance Throughput | Storage Account Throughput |
| 50 | 38  (change to fit maximum storage account throughput) | F2s\_v2  (change to fit whatever size you choose) | 38 \* 80 MBps or ~3 GBps | 25 Gbps or ~3 GBps  (check your specific storage account type and region) |

Page updated 2025-08-20

