---
title: "Viewing Properties"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protected_computers_properties.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Viewing Properties

In this article

You can view detailed information about protected computers. The detailed information provides the following data:

* Hostname
* IP address (for Microsoft Windows-based and Linux-based computers)
* Deployer certificate fingerprint (for Microsoft Windows-based and Linux-based computers)
* SSH fingerprint (for Linux-based computers)
* SSH key algorithm (for Linux-based computers)
* Operating system
* Veeam Agent version
* CBT driver version (for Microsoft Windows-based computers running a Microsoft Windows Server OS)
* Versions of installed Veeam Plug-Ins for enterprise applications (for Microsoft Windows-based and Linux-based computers)
* Versions of Veeam CDP Agent Service and Veeam CDP Volume Filter Driver (for Microsoft Windows-based and Linux-based computers)

|  |
| --- |
| NOTE |
| IP address and Fingerprint information does not apply to members of protection groups for pre-installed Veeam Agents and cloud machines. Key algorithm information does not apply to members of protection groups for pre-installed Veeam Agents. |

To view detailed information about a protected computer:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical and Cloud Infrastructure node.
3. In the working area, select the computer and click Details on the ribbon or right-click the computer and select Details.

![Viewing Properties](images/protected_computer_details.webp)

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
