---
title: "Unix Computers with IBM AIX OS"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pre_installed_agent_upgrade_aix.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Unix Computers with IBM AIX OS


To update pre-installed Veeam Agent on a Unix computer that runs an IBM AIX operating system, perform the following operations:

1. Upload Veeam Agent setup files on the computer you want to protect.

1. Navigate to the directory where you have saved the setup files and install Veeam Agent using the rpm command with the -U parameter. To learn more, see the [Upgrading Product](https://helpcenter.veeam.com/docs/agentforaix/userguide/upgrade_process.html?ver=13) topic in the Veeam Agent for IBM AIX User Guide.

1. If necessary, immediately synchronize Veeam Agent with Veeam Backup & Replication running the following command:

|  |
| --- |
| veeamconfig mode syncnow |


