---
title: "Step 1. Disable Public Access Cosmos DB Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_pne_cosmos_db_disable_public_access.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 1. Disable Public Access Cosmos DB Account


For the Cosmos DB for PostgreSQL account that you want to protect to be inaccessible through public network, you must disable public access to this account:

1. Log in to the [Microsoft Azure portal](https://portal.azure.com).
2. Click More services and select Resource groups on the All services page.
3. On the Resource groups page, select the resource group to which the necessary Cosmos DB for PostgreSQL cluster belongs. The resource group page will open.
4. In the Resource list, locate and click the cluster that you want to protect. The Azure Cosmos DB for PostgreSQL Cluster page will open.
5. Navigate to Settings > Networking.
6. In the Public access section, make sure the Allow public access from Azure services and resources within Azure to this cluster check box is not selected.

[![Disabling Public Access to SQL Server](images/azure_pne_cosmos_db_disable_public.webp)](images/azure_pne_cosmos_db_disable_public.webp "Disabling Public Access to SQL Server")

Page updated 2024-06-27

