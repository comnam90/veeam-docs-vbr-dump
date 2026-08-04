---
title: "Storage Templates"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_storage_template_hiw.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Storage Templates


A storage template is a collection of settings that allows you to define target locations for backups and archived backups. A target location is a backup repository where an SLA-based backup policy stores restore points; it can be the same repository for all AWS Regions protected by the policy, or you can specify separate repositories for each region.

Using region-specific backup repositories allows you to avoid cross-region transaction costs associated with data transfer between AWS Regions during backup and archive operations, while using a single default repository may help you ensure data protection regardless of the source location.

Related Topics

[Adding Storage Templates](aws_storage_add.md)

Page updated 2025-09-03

