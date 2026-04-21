---
title: "Microsoft Azure"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_azure.html"
last_updated: "4/20/2026"
product_version: "13.0.1.2067"
---

# Microsoft Azure


Azure Services

The backup appliance and worker instances must have outbound internet access to a number of Microsoft Azure services. For the list of services, see the Veeam Backup for Microsoft Azure User Guide, section [Azure Services](https://helpcenter.veeam.com/docs/vbazure/guide/azure_services.html?ver=8.1).

Version Compatibility

|  |
| --- |
| Note |
| On February 1, 2025, the Azure AD Graph API service was [retired in Microsoft Azure](https://www.veeam.com/kb4714). As a result, Microsoft Entra applications using Azure AD Graph are no longer able to send requests to Azure AD Graph APIs. That is why Veeam Backup for Microsoft Azure versions prior to version 6.0 are not supported, as these versions use Azure AD Graph. |

The following table lists compatible versions of Veeam Backup & Replication, Veeam Plug-In for Microsoft Azure and Veeam Backup for Microsoft Azure.

Version Compatibility

| Veeam Backup & Replication Build | Veeam Plug-In for Microsoft Azure Build | Veeam Backup for Microsoft Azure Build |
| 12.3.1.1139 | 12.8.0.293 | 8.0.0.334 |
| 12.1.2.172 and later | 12.7.1.18 | 7.1.0.59 |
| 7.1.0.22 |
| 12.7.0.218 | 7.0.0.467 |
| 12.1.0.2131 | 12.6.0.1009 | 6.0.0.234 |
| 12.0.0.1420 | 12.1.5.99 | 5.1.0.75 |
| 12.0.5.740 | 5.0.0.579 |


