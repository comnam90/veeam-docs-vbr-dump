---
title: "Removing SLA and Storage Templates"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sla_storage_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing SLA and Storage Templates


The backup appliance allows you to permanently remove a policy template from the configuration database if you no longer need it:

1. Switch to the Configuration page.
2. Navigate to Policy Templates.
3. Switch to the necessary tab and select the template.
4. Click Remove.

|  |
| --- |
| Important |
| You cannot remove a template that is used by any SLA-based backup policy. [Modify the settings of all the related policies](azure_backup.md) to remove references to the template — and then try removing the template again. |

[![Removing Accounts](images/azure_sla_storage_remove.webp)](images/azure_sla_storage_remove.webp "Removing Accounts")

Page updated 2026-07-01

