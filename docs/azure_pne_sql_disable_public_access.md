---
title: "Step 7. Disable Public Access to SQL Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_pne_sql_disable_public_access.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 7. Disable Public Access to SQL Server


For the SQL Server that you want to protect to be inaccessible through public network, you must disable public access to this SQL Server:

1. Log in to the [Microsoft Azure portal](https://portal.azure.com).
2. Click More services and select Resource groups on the All services page.
3. On the Resource groups page, select the resource group to which the necessary SQL Server belongs. The resource group page will open.
4. In the Resource list, locate and click the SQL Server that you want to protect. The SQL server page will open.
5. Navigate to Security > Networking.
6. In the Public access tab, select the Disable option and click Save.

[![Disabling Public Access to SQL Server](images/azure_pne_sql_disable_public_access.webp)](images/azure_pne_sql_disable_public_access.webp "Disabling Public Access to SQL Server")

Page updated 2024-04-26

