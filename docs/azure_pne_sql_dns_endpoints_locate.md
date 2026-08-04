---
title: "Step 6a. Locate Private Endpoints"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_pne_sql_dns_endpoints_locate.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 6a. Locate Private Endpoints


To locate the automatically created private endpoints, do the following:

1. Log in to the [Microsoft Azure portal](https://portal.azure.com).
2. Click More services and select Resource groups on the All services page.

1. On the Resource groups page, select the resource group to which the necessary storage account belongs. The resource group page will open.
2. In the Resources list, search for storage accounts that are assigned the Veeam backup appliance ID tag.
3. Click the necessary storage account. The Storage account page will open.
4. Navigate to Security + networking > Networking and switch to the Private endpoint connections tab.

[![Locating Private Endpoints](images/azure_private_endpoint_connections.webp)](images/azure_private_endpoint_connections.webp "Locating Private Endpoints")

Page updated 2024-04-25

