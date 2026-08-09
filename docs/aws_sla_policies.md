---
title: "SLA-Based Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_sla_policies.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# SLA-Based Backup Policies


To simplify data protection and monitor compliance with your target SLA, Veeam Plug-in for AWS introduces SLA-based backup policies. An SLA-based backup policy is a collection of settings that automate the way backup operations are performed: how frequently to run the backup process, what region-specific repositories to use to store backups, how many restore points should be created in time to meet SLA requirements, and so on.

To help you eliminate error-prone manual steps and save time configuring SLA-based backup policies, Veeam Plug-in for AWS offers 2 types of templates:

* [SLA template](aws_sla_template_hiw.md) — includes a periodic backup schedule and a target SLA value that you can use to define protection settings for resources processed by SLA-based backup policies.
* [Storage template](aws_storage_template_hiw.md) — includes backup storage settings and region-specific storage options that you can use to define target locations for backups created by SLA-based backup policies.

|  |
| --- |
| Notes |
| * In backup appliance version 10, you can use SLA-based backup policies to protect EC2 instances only.  * SLA-based backup policies are prioritized over schedule-based backup policies. If an EC2 instance is included into both a schedule-based and an SLA-based backup policy, it will be processed by the SLA-based backup policy only. |

For more information on different types of backup policies, see [Protecting EC2 Instances](aws_overview_ec2.md#policies).

Page updated 2026-05-22

