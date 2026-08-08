---
title: "Sizing and Scalability Guidelines"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sizing_guidelines.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Sizing and Scalability Guidelines


This section is intended for professionals who search for a best practice answer to sizing-related issues, and assumes you have already read the whole Veeam Plug-in for Microsoft Azure User Guide.

Be aware that a best practice is not the only answer available. It will fit in the majority of cases but can also be totally wrong under different circumstances. Make sure you understand the implications of the recommended practices, or request assistance. If in doubt, reach out to Veeam professionals on [Veeam R&D Forums](https://forums.veeam.com/veeam-backup-for-azure-f59/).

|  |
| --- |
| Important |
| You must also consider the following:   * The [Azure service quotas](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits) associated with your Microsoft Entra tenants and subscriptions, as well as the performance of [Azure VMs of specific sizes](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes). Some of the options may look good; however, make sure to take into account disk size, speed and burst credits.  * The [performance of Azure Storage accounts](https://docs.microsoft.com/en-us/azure/storage/common/scalability-targets-standard-account) specific to your region. Storage accounts with different redundancy options (LRS, ZRS, GRS) in different regions have different speeds, and there is a maximum throughput per storage account. |

Page updated 2026-07-01

