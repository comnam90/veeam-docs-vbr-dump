---
title: "Step 3. Configure Network Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_workers_add_network.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Step 3. Configure Network Settings


At the Networks step of the wizard, do the following:

1. Click Add to configure worker network interfaces:

1. In the VLAN ID field, specify VLAN ID of a network to which the worker network interface will be connected.
2. In the Description filed, provide a network interface description for future reference.
3. If DHCP is enabled in the selected network, the IP address of the worker can be obtained automatically.

If DHCP is disabled in the selected network, or you want to specify an IP address, select the Use the following IP address option and enter the worker IP address, subnet mask and default gateway.

1. Click OK.

To add more network interfaces, repeat the step and specify the network order using the Up and Down buttons.

1. If DHCP is enabled in any network to which the worker will be connected, DNS settings of the worker can be obtained automatically. To configure DNS settings manually, click Obtain automatically and do the following in the DNS Server Settings window:

1. Select the Use the following DNS server address option.
2. Enter the IP addresses of the preferred and alternate DNS servers.
3. Click OK.

|  |
| --- |
| Note |
| Since workers are Linux-based VMs, they have the same limitations that apply to machines running the Rocky Linux operating system. Therefore, DNS settings cannot be configured separately for each network added to the worker. |

1. To check for available package updates for the worker, Veeam Plug-in for Scale Computing HyperCore automatically connects to Veeam repositories over the internet. If the worker is not connected to the internet, you can instruct Veeam Plug-in for Scale Computing HyperCore to use an HTTP proxy that will provide access to the necessary repositories. To specify HTTP proxy settings, click Advanced and do the following in the Advanced Settings window:

1. Select the Check for updates online check box.
2. From the Internet proxy drop-down list, select Use custom settings.
3. In the Host field, enter the IP address or FQDN of the web proxy.
4. In the Port field, enter the port used on the web proxy for HTTP or HTTPS connections.
5. [Applies only if the HTTP proxy requires authentication] Select the Use authentication check box and select credentials of the account configured on the HTTP proxy to access the internet.

[![Specify Worker Network Settings](images/sch_workers_add_network.webp)](images/sch_workers_add_network.webp "Specify Worker Network Settings")


