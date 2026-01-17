---
title: "Redeploying Network Extension Appliance"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/redeploy_appliance.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---


In this article

The SP can redeploy a network extension appliance for a tenant account. This may be necessary when the network extension appliance becomes inoperative or when the SP changes the password in the network extension appliance credentials record after one or several appliances are already deployed.

To redeploy the network extension appliance:

1. Open the Cloud Connect view.
2. In the inventory pane, click Tenants.
3. In the working area, right-click the necessary tenant and select Properties.
4. At the Network Extension step of the Edit Tenant wizard, in the Network extension appliances section, click Edit and edit settings for the network extension appliance (for example, change the name of the network extension appliance).
5. Click Next to apply new settings. Veeam Backup & Replication will remove a previously deployed network extension appliance and deploy a new network extension appliance VM with new settings. The extension appliance will have root password that is specified in the Credentials Manager.
6. At the Summary step of the wizard, click Finish to exit the wizard.

[![Edit Settings for Network Extension Appliance](images/redeploy_appliance.webp)](images/redeploy_appliance.webp "Edit Settings for Network Extension Appliance")

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
