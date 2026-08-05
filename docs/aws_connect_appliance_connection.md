---
title: "Step 5. Specify Connection Type"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_connect_appliance_connection.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Connection Type


At the Connection Type step of the wizard, specify the way Veeam Backup & Replication will connect to the backup appliance:

* Select the Direct connection option if the backup appliance is connected to a VPC network with the inbound internet access allowed and you want the backup server to connect to this appliance over the internet. In this case, Veeam Backup & Replication will detect the public IP of the appliance automatically.
* Select the Private network option if the backup appliance and the backup server are deployed within the same VPC network, or if the backup appliance is deployed without a public IP address. In this case, you must specify the private IP address or DNS hostname of the backup appliance in the Specify the IP address or DNS name of the appliance field.

Note that you will have to establish connection between the VPC network of the appliance deployed in a private environment and your on-premises network to allow a Veeam Backup & Replication server to communicate with the backup appliance. For more information, see [Backup Appliances in Private Environment](aws_appliance_in_private.md).

![Step 5. Specify Connection Type](images/aws_add_server_connection.webp "Add appliance - Connection")

Page updated 2026-05-20

