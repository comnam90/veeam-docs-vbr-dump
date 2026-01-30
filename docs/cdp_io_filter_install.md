---
title: "Installing I/O Filter"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_io_filter_install.html"
last_updated: "10/23/2025"
product_version: "13.0.1.1071"
---

# Installing I/O Filter


To install the filter on a specific cluster, open the Inventory view. In the inventory pane, navigate to the Virtual Infrastructure > VMware vSphere > vCenter Servers > <vCenter Server Name> > <Cluster Name> node and right-click it. In the menu, select Install I/O filter.

|  |
| --- |
| Important |
| If vSphere LifeCycle Management is enabled for your cluster, you need first follow the instructions from this section and then follow the instructions from [this Veeam KB article](https://www.veeam.com/kb4096). |

To install the I/O filter on multiple clusters in a vCenter Server, use the VeeamCDP Filter Management wizard.

1. [Launch the VeeamCDP Filter Management wizard](cdp_io_filter_launch.md).
2. [Select clusters](cdp_io_filter_cluster.md).
3. [Wait for the filter to be installed](cdp_io_filter_apply.md).
4. [Finish working with the wizard](cdp_io_filter_finish.md).


