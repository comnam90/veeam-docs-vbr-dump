---
title: "Granting User Permissions on Linux and UNIX Machines"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/granting_permissions_rman_linux.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Granting User Permissions on Linux and UNIX Machines

In this article

On Linux and UNIX machines, you can set up access to the plug-in configuration files in command line interface.

By default, the Veeam Plug-In configuration file (veeam\_config.xml) is located in the /opt/veeam/VeeamPluginforOracleRMAN directory on the machine where Veeam Plug-In is installed. To grant access to the configuration file to a dedicated group of users, do the following:

1. Create a new user group by running the following command:

|  |
| --- |
| sudo groupadd <groupName> |

where <groupName> is the name of the created group.

1. Add a user to the group with the following command:

|  |
| --- |
| sudo usermod -a -G +<groupName> <userName> |

where:

* <groupName> — the name of the created group.
* <userName> — the name of the account that will be granted access to the configuration file.

1. Change the ownership of the configuration file to enable users from the dedicated group to access the configuration file. To do this, run the following command:

|  |
| --- |
| sudo chgrp <groupName> /opt/veeam/VeeamPluginforOracleRMAN/veeam\_config.xml |

where <groupName> is the name of the created group.

1. Limit the permissions for the configuration file to allow the read-write access only to the members of the group. To do this, use the following command:

|  |
| --- |
| sudo chmod 660 /opt/veeam/VeeamPluginforOracleRMAN/veeam\_config.xml |

Page updated 9/5/2025

Page content applies to build 13.0.1.1071
