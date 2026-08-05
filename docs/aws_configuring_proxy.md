---
title: "Appendix E. Configuring HTTP Proxy for Backup Appliances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_configuring_proxy.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix E. Configuring HTTP Proxy for Backup Appliances


To manage the outbound traffic from your backup appliance, you can route connections through an HTTP proxy. Using an HTTP proxy helps control access to the required services and resources, enhancing the security, efficiency, and privacy of your backup environment.

|  |
| --- |
| Note |
| The provided instruction does not apply to worker instances that are deployed to perform backup and restore operations, as well as to the Veeam Updater service. To learn how to configure an HTTP proxy for the Veeam Updater service, see [Installing Updates](aws_configuring_updates.md). |

To configure connection to the internet through an HTTP proxy, do the following:

1. To connect to the EC2 instance where the backup appliance is deployed, run the following ssh command in a terminal window:

|  |
| --- |
| ssh -i /path/EC2\_instance.pem key ubuntu@<Public DNS hostname or IPv4 address of the EC2 instance> |

1. To open the configuration file used to set global environment variables, run the following command:

|  |
| --- |
| sudo nano /etc/environment |

1. In the configuration file, do the following:

1. Add a connection through an HTTP proxy server by setting the http\_proxy="http://host:port" variable.
2. [Applies only if the HTTP proxy server requires authentication] Authenticate against the proxy server by setting the http\_proxy="http://username:password@host:port" variable.
3. Specify the IP addresses that must bypass the proxy by setting the NO\_PROXY="<addresses>" variable, where <addresses> is a comma-separated list of necessary IP addresses or DNS names.

The list must include the following addresses: 169.254.169.254 — the IP address of the Instance Metadata Service (IMDS), localhost and 127.0.0.1 — the DNS name and the IP address of your local machine.

1. Save the changes and close the configuration file.

1. To apply the changes without rebooting EC2 instance, run the following command:

|  |
| --- |
| sudo systemctl restart veeamawsbackupweb veeamawsbackuprestfulapi veeamawsbackup veeamawsbackuprestselfbackup |

|  |
| --- |
| Note |
| After you configure the HTTP proxy, backup policies execution may take more time to complete due to network latency. |

Page updated 2026-07-17

