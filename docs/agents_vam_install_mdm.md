---
title: "Installing and Configuring Veeam Agent for Mac with MDM Solution"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_vam_install_mdm.html"
last_updated: "3/31/2026"
product_version: "13.0.1.2067"
---

# Installing and Configuring Veeam Agent for Mac with MDM Solution


You can install and configure Veeam Agent for Mac with a Mobile Device Management (MDM) solution. With an MDM solution, you can connect Veeam Agent to Veeam backup server and include Veeam Agent computer in a protection group.

Veeam Agent for Mac provides the installation package that can be used in the following MDM solutions:

* Jamf Pro
* Microsoft Intune
* SimpleMDM

Veeam Agent for Mac installation and configuration includes the following operations:

1. Installing Veeam Agent.

Only the Veeam Agent for Mac installation package is required.

For details how to deploy a .pkg package, refer to the documentation of your MDM solution.

1. Granting full disk access to Veeam Agent.

To grand full disk access and perform other configuration tasks, you need to use the following Veeam Agent parameters:

* Application ID: NX3JU8SRVL
* Bundle ID: com.veeam.Agent

For other details, refer to the documentation of your MDM solution.

1. Configuring Veeam Agent.

The configuration is required to set up connection between the Veeam Agent computer and the Veeam backup server. To configure Veeam Agent, deploy the device profile for the Veeam backup server on the Veeam Agent computer.

If you use Jamf Pro, Microsoft Intune or SimpleMDM, see detailed instructions in the [Deploying Device Profile with MDM Solution](#profile) subsection. If you use another MDM solution, refer to the documentation of your MDM solution.

Deploying Device Profile with MDM Solution

With an MDM solution, you can connect Veeam Agent to Veeam backup server and include Veeam Agent computer in the protection group in Veeam Backup & Replication. To do this, you must deploy the protection group configuration file as a device profile.

The example below can be used to install Veeam Agent for Mac with Jamf Pro, Microsoft Intune or SimpleMDM. If you use another MDM solution, instructions may differ. For details, refer to the documentation of your MDM solution.

In the example below, the following color coding is applied:

* The yellow parts can be replaced with any values of your choice. Note that UUIDs must be in the UUID format.
* The green part must be copied from the configuration file.

Depending on the MDM solution that you use, select one of the following configuration files:

1. <protection\_group\_name>\_escaped.xml
2. <protection\_group\_name>.xml

where <protection\_group\_name> is the name of the protection group for pre-installed Veeam Agents.

* All other parts must not to be edited.

|  |
| --- |
| <?xml version="1.0" encoding="UTF-8"?> |

After the device profile is deployed on the Veeam Agent computer, Veeam Agent will use the settings from the profile to connect to the Veeam backup server.

Consider that the connection between Veeam backup server and Veeam Agent computer is not persistent. Veeam Agent synchronizes with Veeam Backup & Replication every 6 hours. To synchronize Veeam Agent with Veeam Backup & Replication immediately, run the following command on the Veeam Agent computer:

|  |
| --- |
| veeamconfig mode syncnow |


