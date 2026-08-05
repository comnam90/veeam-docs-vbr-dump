---
title: "Step 8. Specify VPC Interface Endpoint"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_s3_s3endpoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 8. Specify VPC Interface Endpoint


[This step applies only if you have enabled the [private network deployment](aws_enable_private_network_deployment.md) functionality]

At the Settings step of the wizard, specify an S3 interface endpoint that will be used to communicate with the Amazon S3 service.

For an S3 interface endpoint to be displayed in the Interface VPC endpoint list, it must be created in the Amazon VPC console for all subnets to which the worker instances will be connected, as described in section [Configuring Private Networks](aws_configuring_private_networks.md#private_network).

|  |
| --- |
| Important |
| S3 gateway endpoints are not supported when using the private network deployment functionality. |

![Step 8. Specify VPC Interface Endpoint](images/aws_add_s3_endpoint.webp "Add Amazon S3 repository - S3 endpoint")

Page updated 2026-05-20

