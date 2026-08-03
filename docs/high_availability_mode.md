---
title: "Step 2. Specify Cluster Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_mode.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Specify Cluster Mode


At the Cluster Mode step of the wizard, select the desired cluster configuration mode.

1. In the Cluster mode section, select the desired mode

* Standard HA cluster mode — deploys the HA cluster within a single subnet. Select this option for local environments where all cluster nodes reside on the same network.
* Cross-subnet HA cluster mode — deploys the HA cluster across multiple subnets. Select this option for environments that require disaster recovery and site resilience, where cluster nodes span different networks or geographic locations.

![Step 2. Specify Cluster Mode](images/high_availability_mode.webp)

Page updated 2026-06-26

