---
title: "Backup Appliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sizing_appliance.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Appliance


You can choose the size of the Azure VM running Veeam Backup for Microsoft Azure during the deployment, or change it later as the environment grows.

|  |
| --- |
| Note |
| In Veeam Backup for Microsoft Azure version 13, you can only choose the B2ms, F4s\_v2 or F8s\_v2 VM size. |

General Recommendations

The following recommendations and examples apply to the latest backup appliance builds.

General Recommendations

| Azure VM Size | Recommended Maximum Number of Protected Workloads | Recommended Maximum Number of Launched Worker Instances |
| B2ms (2 vCPU, 8 GB RAM)  Note: The minimum amount of system RAM recommended to perform [Virtual Network configuration backup](azure_overview_vnet.md) is 8 GB. If you plan to protect Azure Virtual Network configuration components, it is not recommended that you choose the B2s Azure VM size — consider choosing larger sizes. | * 500 * 300 (if backed up simultaneously) | 20 |
| F4s\_v2 (4 vCPU, 8 GB RAM) | * 1,500 * 500 (if backed up simultaneously) | 150 |
| F8s\_v2 (8 vCPU, 16 GB RAM) | * 3,000 * 1,500 (if backed up simultaneously) | 300 |

|  |
| --- |
| Note |
| For product deployments running on Azure VMs whose size is larger than D4s\_v3, Veeam Backup for Microsoft Azure may simultaneously launch 100 worker instances per region — however, this can trigger throttling issues in Microsoft Azure. If you are facing these issues, it is recommended that you use a maximum of 70 worker instances per region at a time. Alternatively, consider reducing the number of worker instances launched simultaneously by configuring different schedules for your backup policies or by specifying different target regions. For more information, see [Performing Backup](azure_backup.md). |

Veeam Backup & Replication Integration

When you connect a backup appliance to the backup infrastructure, its backup policies, cloud-native snapshots, image-level backups, backup repositories and sessions are imported into the Veeam Backup & Replication database.

You can connect multiple backup appliances to a single Veeam Backup & Replication server. However, when working in an Azure subscription with cross-region data transfer, it is recommended that you use one Veeam Backup & Replication server per region, to help you avoid latency issues and meet potential data residency regulations.

Page updated 2026-07-01

