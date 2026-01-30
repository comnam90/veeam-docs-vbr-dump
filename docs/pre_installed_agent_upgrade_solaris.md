---
title: "Unix Computers with Oracle Solaris OS"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pre_installed_agent_upgrade_solaris.html"
last_updated: "2/23/2024"
product_version: "13.0.1.1071"
---

# Unix Computers with Oracle Solaris OS


To update pre-installed Veeam Agent on a Unix computer that runs an Oracle Solaris operating system, perform the following operations:

1. Upload Veeam Agent setup files on the computer you want to protect.

1. Navigate to the directory where you have saved the setup files and install Veeam Agent. This procedure is similar to the default installation of the Veeam Agent for Oracle Solaris. To learn more, see the [Installing Veeam Agent for Oracle Solaris](https://helpcenter.veeam.com/docs/agentforsolaris/userguide/install_solaris.html?ver=13) topic in the Veeam Agent for Oracle Solaris User Guide.

1. If necessary, immediately synchronize Veeam Agent with Veeam Backup & Replication running the following command:

|  |
| --- |
| veeamconfig mode syncnow |


