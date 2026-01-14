---
title: "Step 2. Specify Cluster Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_configuration_endpoint.html"
last_updated: "11/5/2025"
product_version: "13.0.1.1071"
---

# Step 2. Specify Cluster Settings

In this article

At the Cluster Endpoint step of the wizards, specify the cluster name and a virtual IP address of the cluster.

1. In the Cluster DNS name field, specify a DNS name of a cluster.

|  |
| --- |
| Note |
| If you would like to use the DNS name to access your cluster, you must configure this DNS name to resolve to the сluster IP address. |

1. In the Virtual IP address field, specify the static IP address of a cluster. Veeam Backup & Replication will assign this IP address to the primary node.

![Step 2. Specify Cluster Settings](images/high_availability_cluster_endpoint.webp)

Page updated 11/5/2025

Page content applies to build 13.0.1.1071
