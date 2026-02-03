---
title: "Adding Nutanix AHV Server to Backup Infrastructure"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_add_ahv_cluster.html"
last_updated: "1/9/2026"
product_version: "13.0.1.1071"
---

# Adding Nutanix AHV Server to Backup Infrastructure


To add a Nutanix AHV cluster or Prism Central to the backup infrastructure, do the following:

1. [Launch the New Nutanix AHV Server wizard](ahv_add_ahv_launch.md).
2. [Specify the Nutanix AHV server domain name or IP address](ahv_add_ahv_name.md).
3. [Enter credentials to access the Nutanix AHV cluster](ahv_add_ahv_credentials.md).
4. [Apply Nutanix AHV server settings](ahv_add_ahv_apply.md).
5. [Finish working with the wizard](ahv_add_ahv_finish.md).

Considerations and Limitations

After you add a Prism Central to the backup infrastructure, consider the following:

* If some Prism Central clusters were already added to the backup infrastructure as standalone clusters, they will be automatically configured as clusters registered with the Prism Central.For more information on, see [Prism Central Deployment Scenario](ahv_infrastructure_prism_central.md).
* If you register a new cluster with the Prism Central, Veeam Backup & Replication will automatically add it to the backup infrastructure and you will be able to protect resources in this cluster. For more information, see sections [Performing Backup](ahv_data_protection.md) and [Performing Restore](ahv_data_recovery.md).
* If you unregister an existing cluster from the Prism Central, you will not be able to protect resources in this cluster anymore. To protect these resources, you can add the cluster to the backup infrastructure as a standalone cluster. For more information, see [Solution Architecture](ahv_infrastructure_components.md).


