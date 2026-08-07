---
title: "Step 6. Configure Automatically Created Private Endpoints"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_pne_sql_dns_endpoints.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 6. Configure Automatically Created Private Endpoints


For Veeam Backup for Microsoft Azure to be able to establish private connections with the protected Azure VMs, you must configure DNS settings for private endpoints that Veeam Backup for Microsoft Azure automatically created in Microsoft Azure at [step 5](azure_app_pne_first_policy_run.md). Private endpoints are network interfaces that use private IP addresses from VNets. For more information on private endpoints, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/storage/common/storage-private-endpoints).

To configure DNS settings for private endpoints, perform the following steps:

1. [Locate private endpoints for your Veeam storage account in Microsoft Azure](azure_pne_sql_dns_endpoints_locate.md).
2. [Configure the private endpoint for Azure Blob Storage](azure_pne_sql_dns_endpoints_blobs.md).
3. [Configure private endpoint for Azure Queue Storage](azure_pne_sql_dns_endpoints_queues.md).

Page updated 2024-05-14

