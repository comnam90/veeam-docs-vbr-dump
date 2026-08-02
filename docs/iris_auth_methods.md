---
title: "Authentication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_auth_methods.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Authentication


Epic EHR System Protection in Veeam Backup & Replication requires two types of credentials: credentials to connect to ODB servers for deploying and communicating with Veeam components, and a user name for the InterSystems IRIS instance owner to access each InterSystems IRIS instance for application-aware processing during backup. You configure each type at a different point in the setup workflow.

|  |
| --- |
| Important |
| Before you configure Epic EHR System Protection protection, consider the access permissions listed in [Permissions](iris_plan_and_manage_permissions.md). |

Connecting to ODB Servers

When Veeam Backup & Replication connects to an ODB server to deploy Veeam components or collect topology information, it uses one of the following methods depending on the settings specified in the protection group configuration:

* Admin credentials — Veeam Backup & Replication connects to the ODB server over SSH using a stored or single-use account with root privileges. Veeam Backup & Replication uses this account to deploy the Veeam Transport service and the InterSystems IRIS plug-in, and to install the TLS certificate. This is the default connection method.
* Certificate-based authentication — Veeam Backup & Replication connects to the ODB server using a TLS certificate and communicates with the Veeam Installer Service pre-installed on the server. Select this method if you have deployed the Deployment Kit on the ODB server in advance. No SSH connection or stored credentials are required.

You configure the connection method individually for each ODB server at the ODB Servers step of the New Protection Group wizard. For details, see [Specify ODB Servers](iris_protection_group_odb_servers.md).

Accessing InterSystems IRIS Instances

To perform application-aware processing, including freezing and thawing the InterSystems IRIS instance before and after the storage snapshot, Veeam Backup & Replication connects to the InterSystems IRIS instance through the Veeam Transport service already running on the ODB server and switches to the database user that owns the instance. No password is required because the connection goes through the Transport service, which is already authenticated on the ODB server. Veeam Backup & Replication does not use SSH for this step.

You must specify the instance owner user name at the Instance processing step of the New Application Backup Policy wizard. You can specify a different user name for each instance or apply one user name to all instances in the backup scope. For details, see [Specify Processing Settings](iris_policy_processing.md).

|  |
| --- |
| NOTE |
| If Veeam Backup & Replication cannot find the specified user on the ODB server, or if the user does not have the necessary privileges to run InterSystems IRIS commands, the backup policy session fails with an authentication error. Make sure that the user name you specify is configured for authentication for the InterSystems IRIS instance. |

Page updated 2026-07-29

