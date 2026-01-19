---
title: "Veeam Plug-in for VMware Cloud Director"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_plugin_upload_configure.html"
last_updated: "12/11/2025"
product_version: "13.0.1.1071"
---

# Veeam Plug-in for VMware Cloud Director


Veeam Plug-in for VMware Cloud Director lets members of VMware Cloud Director organizations access Veeam Self-Service Backup Portal from the native VMware Cloud Director environment.

You can upload and configure the plug-in in VMware Cloud Director Service Provider Admin Portal. When you upload the plug-in, you specify the scope — a set of Cloud Director organizations that can use the plug-in.

If you need to modify the scope of Cloud Director organizations after you configure the plug-in, update the plug-in configuration. For more information, see [Updating Plug-in Configuration](#update).

|  |
| --- |
| Important |
| In VMware Cloud Director Service Provider Admin Portal, you cannot upgrade plug-ins. To switch to a newer version of Veeam Plug-in for VMware Cloud Director, delete the current plug-in version and then upload a newer one. For more information on deleting the plug-in, see the [Delete a Plug-in From Your VMware Cloud Director](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/vmware-cloud-director/10-5/delete-a-vcd-plug-in.html) section of the VMware Cloud Director documentation. For details on uploading the plug-in, see [Uploading and Configuring Plug-in](#upload_and_configure).  Before you delete the plug-in, make a note of the Cloud Director organizations that are allowed to use the plug-in. For more information on how to view them, see the [Publish or Unpublish a Plug-in from an Organization](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/vmware-cloud-director/10-5/publishor-unpublish-a-vcd-plug-in-to-an-organization.html) section of the VMware Cloud Director documentation. |

Before You Begin

Before you start uploading Veeam Plug-in for VMware Cloud Director, check the following prerequisites:

* Members of Cloud Director organizations using the plug-in must have network access to the Cloud Director server and Veeam Backup Enterprise Manager server.

You specify the Veeam Backup Enterprise Manager server URL in Cloud Director Service Provider Admin Portal when you configure the plug-in. For more information, see [Uploading and Configuring Plug-in](#upload_and_configure).

* The Veeam Backup Enterprise Manager server should use a certificate issued by a Certificate Authority instead of a default self-signed certificate. In case of a self-signed certificate, users of the plug-in have to add the Enterprise Manager certificate as trusted to their browser before they access the plug-in. Otherwise, they will get a connection error.

For more information on the Enterprise Manager certificate, see [Installing Certificates](updating_security_certificate.md).

Uploading and Configuring Plug-in

To upload and configure Veeam Plug-in for VMware Cloud Director, follow these steps:

1. Log in to VMware Cloud Director Service Provider Admin Portal under a Cloud Director system administrator account.
2. Upload the plugin.zip file to the portal. You can download the file from the Additional Downloads section at [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html) or [my.veeam.com](https://my.veeam.com/my-products).

For more information, see the [Upload a Plug-in to Your VMware Cloud Director](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/vmware-cloud-director/10-5/upload-a-vcd-plug-in.html) section of the VMware Cloud Director documentation.

1. From the More menu, select Data Protection with Veeam.

If the Data Protection with Veeam option is not available, log out of the VMware Cloud Director Service Provider Admin Portal and log in again.

1. In the Plug-in Configuration section, specify the URL to the Veeam Backup Enterprise Manager server, for example: https://hostname:443.
2. Click Save.

|  |
| --- |
| Note |
| When you save the plug-in configuration, it is applied to all Cloud Director organizations. For that, a separate operation is performed for each organization. If you have operation limits that are set through the VMware Cloud Director API, the operations may fail with HTTP status 400.  In this case, use the VMware Cloud Director API to set the QueuedOperationsPerOrg and QueuedOperationsPerUser elements to zero until you save the plug-in configuration. For more information, see the [OperationLimitsSettingsType](https://developer.vmware.com/apis/1751/doc/types/OperationLimitsSettingsType.html) section of VMware Cloud Director API documentation. |

1. [For Microsoft Windows-based Enterprise Manager] On the Enterprise Manager server in IIS Manager, recycle the VeeamBackup application pool.

For more information, see the [Recycling Settings for an Application Pool <recycling>](https://docs.microsoft.com/en-us/iis/configuration/system.applicationhost/applicationpools/add/recycling/) section of Microsoft Docs.

Updating Plug-in Configuration

After you configure the plug-in, you can modify the scope of Cloud Director organizations. It may be useful, for example, if you create a new Cloud Director organization and you want members of this organization to use the plug-in. To include or exclude Cloud Director organizations, update the plug-in configuration.

To update the plug-in configuration:

1. Log in to VMware Cloud Director Service Provider Admin Portal under a Cloud Director system administrator account.
2. Modify the scope of Cloud Director organizations.

For more information, see the [Publish or Unpublish a Plug-in from an Organization](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/vmware-cloud-director/10-5/publishor-unpublish-a-vcd-plug-in-to-an-organization.html) section of the VMware Cloud Director documentation.

1. From the More menu, select Data Protection with Veeam.
2. In the Plug-in Configuration section, click Save to apply the changes to all Cloud Director organizations.


