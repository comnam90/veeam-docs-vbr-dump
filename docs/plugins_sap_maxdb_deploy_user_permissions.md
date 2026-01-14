---
title: "Granting Permissions to Users"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_user_permissions.html"
last_updated: "10/31/2025"
product_version: "13.0.1.1071"
---

# Granting Permissions to Users

In this article

When you install Veeam Plug-In for SAP MaxDB, full access rights to the plug-in configuration file are automatically granted to all users. To protect sensitive information that is stored in the configuration file from unwanted access, we recommend limiting access to the configuration file to a dedicated group of users.

Before You Begin

Before you create a user group that will have access to the plug-in configuration file, consider the following:

* To perform this procedure, your OS user account must have root privileges.
* After a user is added to the group, the user must log out, then log in to the Linux OS again to activate the group permissions.
* Add only trusted users to the group.

|  |
| --- |
| Important |
| The user that configures the plug-in must be added to the group. As a rule, this user is ora<dbsid> or root, but the root user account has access to all files in the system and does not need to be added to the group. |

Granting Permissions to the Plug-In Configuration File

By default, the Veeam Plug-In configuration file (veeam\_config.xml) is located in the /opt/veeam/VeeamPluginforSAPMaxDB directory on the machine where Veeam Plug-In is installed. To grant access to the configuration file to a dedicated group of users, do the following:

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
| sudo chgrp <groupName> /opt/veeam/VeeamPluginforSAPMaxDB/veeam\_config.xml |

where <groupName> is the name of the created group.

1. Limit the permissions for the configuration file to allow the read-write access only to the members of the group. To do this, use the following command:

|  |
| --- |
| sudo chmod 660 /opt/veeam/VeeamPluginforSAPMaxDB/veeam\_config.xml |

Page updated 10/31/2025

Page content applies to build 13.0.1.1071
