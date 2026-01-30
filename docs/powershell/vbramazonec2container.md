---
title: "VBRAmazonEC2Container"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbramazonec2container.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRAmazonEC2Container


Contains Amazon EC2 entities.

| Property | Type | Description |
| --- | --- | --- |
| Region | [VBRAmazonS3Region](vbramazons3region.md) | AWS Region and datacenter. |
| Entity | Object[] | EC2 instances, EC2 tags or AWS datacenters. |
| ExcludeEntities | Bool | Excludes EC2 instances, EC2 tags or AWS datacenters. |
| Excluded Entity | Object[] | Excluded EC2 instances, EC2 tags or AWS datacenters. |
| AutoAssignIAMRole | Bool | Assigns IAM role with the AmazonSSMManagedInstanceCore policy to all EC2 instances. |


