---
title: "Backup Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sizing_object_storage.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Repository


Backup appliances compress all backed-up data when saving it to backup repositories. The compression rate depends on the type and structure of source data and usually varies from 50% to 60%. This means that the compressed data typically consumes 50% less storage space than the source data.

Backup Repository

| Parameter | Value |
| Average size of backed-up data | 40%–50% of source data |
| Compression rate | 50%–60% |

Object Sizes

Depending on whether you choose to keep backed-up data in short-term or long-term storage, backup appliances save different objects to Azure blob containers.

Object Sizes

| Object Type | Block Size |
| Backup data (hot and cool tiers) | 1 MB (compressed to ~512 KB) |
| Backup data (archive tier) | 512 MB |
| Metadata | 4 KB (per 1 GB of VM source data) |

Storage Account Limits

Storage accounts have [throughput limits](https://docs.microsoft.com/en-us/azure/storage/common/scalability-targets-standard-account) that vary per region. It is recommended that you configure multiple repositories for a single Veeam Backup for Microsoft Azure deployment, or even, in some cases, one per policy. This changes regularly, currently these limits are:

Storage Account Limits

| Resource | Limit |
| Default maximum request rate per storage account | 20K IOPS (~512 KB block size) |
| Default maximum write speed in large regions | 60 Gbps |
| Default maximum write speed in other regions | 25 Gbps |
| Default maximum write speed for legacy storage accounts | 10 Gbps |

Cost Estimation

Backup appliances come with a built-in cost calculator that allows you to estimate your Azure expenses. It uses publicly available Microsoft Azure price lists, so it may not reflect your exact cost in case of custom pricing or an enterprise agreement. Full details can be found at the cost estimation step of the Add Policy wizard.

Page updated 2026-07-01

