---
title: "Managing Domain Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hmc_configure_domain.html"
last_updated: "2/17/2026"
product_version: "13.0.1.1071"
---

# Managing Domain Settings


In the Veeam Host Management web UI, you can change domain membership of the server. To do this, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Network.
3. In the Domain section, select one of the following options:

* If the server is not a part of a domain, click Change domain. In the Join Domain window, specify the domain name and credentials with domain joining permissions. Then, click Save.

|  |
| --- |
| Note |
| It is recommended to specify the domain name instead of the FQDN of a specific domain controller. This can mitigate domain joining issues if this domain controller is unavailable for some reason. |

* If the server is a part of a domain, click Leave domain and confirm the operation.

After you change the domain membership, all services running on the server will be restarted. If you change the domain membership of the backup server that has running jobs, backup or recovery operations performed by these jobs will fail.

To specify additional DNS suffixes, click Configure next to the setting name.

[![Managing Domain Settings](images/hmc_web_change_domain.webp)](images/hmc_web_change_domain.webp)


