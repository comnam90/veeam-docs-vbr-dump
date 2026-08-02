---
title: "Creating Private Endpoints"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_app_pne_storage_endpoints.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Creating Private Endpoints


If the backup appliance resides in another region than the resources that you want to back up, or you do not want to add firewall rules, you can create private endpoints for your storage account to allow Veeam Backup for Microsoft Azure access to the resources.

You must create a separate private endpoint for every VNet to which the backup appliance or worker instances are connected. To create a private endpoint, perform the following steps:

1. [Launch the Create a private endpoint wizard](azure_app_pne_storage_wizard.md).
2. [Configure general settings for the private endpoint](azure_app_pne_storage_endpoint.md).
3. [Specify resource settings](azure_app_pne_storage_resource.md).
4. [Specify virtual network settings](azure_app_pne_storage_configuration.md).
5. [Specify DNS settings](azure_app_pne_storage_dns.md).
6. [Assign tags](azure_app_pne_storage_tags.md).
7. [Finish working with the wizard](azure_app_pne_storage_finish.md).
8. [Configure network settings of the newly created private endpoint](azure_pne_storage_peering.md).

Page updated 2024-08-27

