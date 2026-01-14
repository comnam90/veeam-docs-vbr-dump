---
title: "Linux Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pre_installed_agent_upgrade_linux.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Linux Computers

In this article

To update pre-installed Veeam Agent on a Linux computer, perform the following operations:

1. Upload Veeam Agent setup files on the computer you want to protect.

1. Navigate to the directory where you have saved setup files and install Veeam Agent. This procedure is similar to the installation of the Veeam Agent for Linux in the offline mode. To learn more, see the [Installing Veeam Agent for Linux in Offline Mode](https://helpcenter.veeam.com/docs/agentforlinux/userguide/installation_offline.html) section in the Veeam Agent for Linux User Guide.

1. If necessary, immediately synchronize Veeam Agent with Veeam Backup & Replication running the following command:

|  |
| --- |
| veeamconfig mode syncnow |

Page updated 8/29/2025

Page content applies to build 13.0.1.1071
