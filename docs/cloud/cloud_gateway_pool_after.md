---
title: "What You Do Next"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_gateway_pool_after.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# What You Do Next


After you create a cloud gateway pool, you must do the following:

1. Assign the created cloud gateway pool to the tenant in the properties of the tenant account. To learn more, see [Specify Bandwidth Settings](cloud_connect_user_throttling.md).
2. Pass to the tenant a DNS name or IP address of one or more cloud gateways added to the cloud gateway pool.

Only those tenants to whom the cloud gateway pool is assigned can use cloud gateways added to this cloud gateway pool. Other tenants will be able to use individual cloud gateways that are not added to any cloud gateway pool.


