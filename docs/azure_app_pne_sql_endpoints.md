---
title: "Step 8. Create Private Endpoint for SQL Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_sql_endpoints.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 8. Create Private Endpoint for SQL Server


To allow Veeam Backup for Microsoft Azure access to the databases that you want to protect, you must create private endpoints for your SQL Server.

You must create a separate private endpoint for every VNet to which worker instances are connected. To create a private endpoint, complete the following steps:

1. [Launch the Create a private endpoint wizard](azure_app_pne_sql_wizard.md).
2. [Configure private endpoint settings](azure_app_pne_sql_endpoint.md).
3. [Specify resource settings](azure_app_pne_sql_resource.md).
4. [Specify network settings](azure_app_pne_sql_configuration.md).
5. [Specify DNS settings](azure_app_pne_sql_dns.md).
6. [Assign tags](azure_app_pne_sql_tags.md).
7. [Finish working with the wizard](azure_app_pne_sql_finish.md).

Page updated 2024-08-27

