---
title: "Changing Server Name"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hmc_configure_hostname.html"
last_updated: "2/20/2026"
product_version: "13.0.1.1071"
---

# Changing Server Name


Before you change the server name, consider the following:

* If the server is a part of the domain, remove the server from the domain first. For more information on how to do it, see [Managing Domain Settings](hmc_configure_domain.md).
* After you change the name, all services running on the server will be restarted. If you change the name of the backup server that has running jobs, backup or recovery operations performed by these jobs will fail.

If you use the Veeam Host Management web UI, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Network.
3. In the Hostname section, click Edit.
4. Specify a new server name.
5. Click OK.

[![Changing Server Name](images/hmc_web_change_hostname.webp)](images/hmc_web_change_hostname.webp)

If you use the Veeam Host Management TUI, perform the following steps:

1. Log in to the Veeam Host Management TUI as a Host Administrator.
2. In the main menu, select Host configuration > Hostname.
3. Specify a new server name and press [Enter].

[![Changing Server Name](images/hmc_tui_change_hostname.webp)](images/hmc_tui_change_hostname.webp)


