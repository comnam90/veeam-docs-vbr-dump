---
title: "Installing Veeam Agent"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protected_computers_install.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Installing Veeam Agent


You can install Veeam Agent on a specific protected computer in the inventory. This operation may be required, for example, if you want to test the installation process before allowing Veeam Backup & Replication to deploy Veeam Agent to all computers included in the protection group.

Keep in mind that Veeam Agents for computers that you plan to add to a protection group for pre-installed Veeam Agents require a different installation approach. To learn more, see [Deploy Veeam Agents](pg_pre_installed_next.md).

Before you install Veeam Agent, check the following prerequisites:

* The protected computer must be powered on and able to be connected over the network.

* The required version of Veeam Agent must be available on the distribution server.

In some cases, installation of Veeam Agent for Microsoft Windows may require computer reboot. This can happen, for example, if you have earlier versions of .NET runtimes installed on the computer and during the installation process the framework is used by third-party software. You can instruct Veeam Backup & Replication to automatically reboot the Veeam Agent computer. To do so, select the Perform reboot automatically if required check box in the [protection group settings](agents_protection_group_options.md).

|  |
| --- |
| TIP |
| To prevent protected computers from being compromised, Veeam Backup & Replication validates the integrity and authenticity of the Veeam Agent installation package before uploading it to the computer. |

You can install Veeam Agent on a protected computer in the following ways:

* [Installing Veeam Agent Using Console](#console)
* [Installing Veeam Agent Using Web UI](#webui)

Installing Veeam Agent Using Veeam Backup & Replication Console

To install Veeam Agent on a protected computer in the Veeam Backup & Replication console:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical and Cloud Infrastructure node and select the necessary protection group.
3. In the working area, select the necessary computer and click Install Agent on the ribbon or right-click the computer and select Agent > Install agent.

[![Install Veeam Agent](images/protected_computer_agent.webp)](images/protected_computer_agent.webp "Install Veeam Agent")

Installing Veeam Agent Using Veeam Backup & Replication Web UI

To install Veeam Agent on a protected computer in the Veeam Backup & Replication web UI:

1. In the management pane, click Protection Groups.
2. Select the protection group that contains the necessary computer.
3. In the working area, select the check box next to the computers and click Install > Install Backup Agent on the toolbar. Alternatively, right-click the computer and select Install > Install Backup Agent.

[![Install Veeam Agent](images/protected_computer_install_web.webp)](images/protected_computer_install_web.webp "Install Veeam Agent")

Page updated 2026-07-06

