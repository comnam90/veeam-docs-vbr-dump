---
title: "Step 3. Specify Data Retrieval Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_volume_data_retrieval.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Data Retrieval Settings


[This step applies only if you have selected to restore from the archived restore point]

At the Data Retrieval step of the wizard, choose a retrieval mode and specify a period for which you want to keep the data available. To do that:

1. In the Retrieval mode section, click the link.

1. In the Retrieval settings window, for each processed EC2 instance, do the following:

1. Select an EC2 instance and click Edit.
2. In the Edit Retrieval Mode window, select the retrieval mode that the backup appliance will use to retrieve the archived data, and click Save. For more information on data retrieval modes, see [Retrieving EC2 Data From Archive](aws_data_retrieval.md).

1. To save changes made to the data retrieval settings, click Apply.

[![Restoring EBS Volumes](images/aws_restore_volume_retrieval_mode.webp)](images/aws_restore_volume_retrieval_mode.webp "Restoring EBS Volumes")

1. In the Availability period section, click Edit Availability Period.

1. In the Availability settings window, specify the number of days for which you want to keep the data available for restore operations. If the time period expires while a restore operation is still running, the backup appliance automatically extends the period to keep the retrieved data available for 1 more day. You can also [manually extend the availability period](aws_data_retrieval.md#extend) later if required.
2. To save changes made to the availability period settings, click Apply.

[![Restoring EBS Volumes](images/aws_restore_volume_availability_period.webp)](images/aws_restore_volume_availability_period.webp "Restoring EBS Volumes")

Page updated 2026-05-22

