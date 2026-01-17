---
title: "Creating Kasten Policies"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/add_policy.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

To export backups of applications to Veeam backup repositories, you must create Veeam Kasten policies and define the necessary settings in the Veeam Kasten dashboard associated with your Veeam Kasten cluster.

To create a Veeam Kasten policy, open the Veeam Kasten dashboard and perform the following steps:

1. Configure Veeam Backup repository location.

At the location profile settings, specify the Veeam Backup & Replication server and the Veeam backup repository that will keep backups exported by Veeam Kasten policies. For more information, see [Veeam Kasten Docs](https://docs.kasten.io/latest/usage/configuration.html#veeam-backup-repository-location).

1. Configure Kasten policy.

In the Veeam Kasten dashboard, configure a policy and select the necessary Veeam backup location profile. Veeam Kasten will export backups of applications from the Veeam Kasten cluster to the Veeam backup repository according to these settings. For more information, see [Kasten Docs](https://docs.kasten.io/latest/usage/protect.html).

After you configure the Veeam Kasten policy, it appears in the Veeam Backup & Replication infrastructure.

Page updated 8/26/2024

Page content applies to build 13.0.1.1071
