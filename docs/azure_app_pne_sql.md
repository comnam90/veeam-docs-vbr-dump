---
title: "Configuring Network Settings for SQL Servers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_sql.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Configuring Network Settings for SQL Servers


To allow Veeam Backup for Microsoft Azure to back up SQL Servers in a private environment, perform the following steps:

1. [Create private DNS zones](azure_pne_sql_dns_zones.md).
2. [Add a custom worker configuration](azure_pne_sql_worker_configuration.md).
3. [Add the VNets of the backup appliance and worker instances to the private DNS zones](azure_pne_sql_add_vnets_to_dns_zones.md).
4. [Configure network settings for backup appliance](azure_pne_sql_peering.md).
5. [Create and run a backup policy to automatically create storage accounts and private endpoints](azure_pne_sql_first_policy_run.md).
6. [Configure automatically created private endpoints](azure_pne_sql_dns_endpoints.md).
7. [Disable public access to the SQL Server](azure_pne_sql_disable_public_access.md).
8. [Create a private endpoint for the SQL Server](azure_app_pne_sql_endpoints.md).
9. [Configure the private endpoint created for the SQL Server](azure_pne_sql_manual_endpoint.md).
10. [Run the backup policy to check whether the configuration was successful](azure_pne_sql_test_policy_run.md).

Page updated 2024-05-14

