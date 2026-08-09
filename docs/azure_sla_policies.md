---
title: "SLA-Based Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sla_policies.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# SLA-Based Backup Policies


To simplify data protection and monitor compliance with your target SLA, Veeam Plug-in for Microsoft Azure introduces SLA-based backup policies. An SLA-based backup policy is a collection of settings that automate the way backup operations are performed: how frequently to run the backup process, what region-specific repositories to use to store backups, how many restore points should be created in time to meet SLA requirements, and so on.

To help you eliminate error-prone manual steps and save time configuring SLA-based backup policies, Veeam Plug-in for Microsoft Azure offers 2 types of templates:

* [SLA template](azure_sla_template_hiw.md) — includes a periodic backup schedule and a target SLA value that you can use to define protection settings for workloads processed by SLA-based backup policies.
* [Storage template](azure_storage_template_hiw.md) — includes backup storage settings and region-specific storage options that you can use to define target locations for backups created by SLA-based backup policies.

|  |
| --- |
| Notes |
| * In backup appliance version 8.1, you can use SLA-based backup policies to protect Azure VMs only. * Veeam Backup for Microsoft Azure prioritizes SLA-based backup policies over schedule-based backup policies. If an Azure VM is included into both a schedule-based and an SLA-based backup policy, it will be processed by the SLA-based backup policy only. |

For more information on different types of backup policies, see [Protecting Azure VMs](azure_overview_vm.md).

Page updated 2026-07-01

