---
title: "Appendix A. Configuring HTTP Proxy for Backup Appliances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuring_http_proxy.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix A. Configuring HTTP Proxy for Backup Appliances


To manage the inbound and outbound traffic of your backup appliance, you can route connections through an HTTP proxy. Using an HTTP proxy provides access to the required services and resources, enhancing the security, efficiency and privacy of your backup environment.

|  |
| --- |
| Note |
| The provided instruction does not apply to worker instances that are deployed to perform backup and restore operations, as well as to the Veeam Updater service. To learn how to configure connection to an HTTP proxy for the Veeam Updater service, see [Installing Updates](azure_configuring_updates.md). |

To configure connection to the internet through an HTTP proxy, do the following:

1. On the Azure VM on which Veeam Backup for Microsoft Azure is installed, open the configuration file used to set global environment variables by running the following command in a terminal window:

|  |
| --- |
| sudo nano /etc/environment |

1. In the configuration file, do the following:

1. Add a connection through an HTTP proxy server by setting the http\_proxy="http://host:port" variable.
2. Add a connection through an HTTPS proxy server by setting the https\_proxy="http://host:port" variable.

The https\_proxy variable must have the same HTTP proxy address specified in its value as the http\_proxy variable.

|  |
| --- |
| Important |
| Veeam Backup for Microsoft Azure does not support access to resources through HTTPS proxy. The https\_proxy variable is used only to ensure that the HTTPS traffic is sent to the HTTP proxy. |

1. [Applies only if the proxy server requires authentication] To authenticate against the proxy server, set the variables http\_proxy="http://username:password@host:port" and https\_proxy="http://username:password@host:port".
2. Specify the IP addresses that are not required to use the proxy to connect to your backup appliance by setting the NO\_PROXY="<addresses>" variable, where <addresses> is a comma-separated list of necessary IP addresses or DNS names.

The list must include the following addresses: 169.254.169.254 — the IP address of the Azure Instance Metadata Service (IMDS), localhost and 127.0.0.1 — the DNS name and the IP address of your local machine.

1. Save the changes and close the configuration file.

1. To apply changes, reboot the Azure VM on which Veeam Backup for Microsoft Azure is installed.
2. Use either Azure network security groups or firewall rules to allow inbound and outbound access to the Azure VM on which Veeam Backup for Microsoft Azure is installed for all necessary IP addresses including those of your backup server, the HTTP proxy itself, IMDS, and so on.

|  |
| --- |
| Important |
| * For Veeam Backup for Microsoft Azure to be able to create and manage repositories when using the configured HTTP proxy, open a [support case](azure_support_information.md). * The provided instruction applies to backup appliances that operate public virtual networks. If you want to use an HTTP proxy for a backup appliance deployed in a private environment, open a [support case](azure_support_information.md). * Veeam Backup for Microsoft Azure version 13 does not support connection to email server specified in the notification settings through an HTTP proxy. If you plan to configure these settings, you must allow inbound and outbound access to the Azure VM on which Veeam Backup for Microsoft Azure is installed for the necessary email server. |

Page updated 2026-07-30

