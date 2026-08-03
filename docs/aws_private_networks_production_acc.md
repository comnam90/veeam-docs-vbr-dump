---
title: "Configuring Private Networks for Production Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_private_networks_production_acc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Private Networks for Production Accounts


If you have multiple AWS accounts and want to deploy worker instances in [production accounts](aws_worker_options.md#production), the estimated cost of VPC endpoints per account may occur to be significantly high. To reduce the cost, you can create a single resource share in one AWS account for all subnets to which the worker instances will be connected, and share the resource with other AWS accounts belonging to the same organization.

For backup appliances to be able to deploy worker instances in a private environment in production accounts, perform the following steps:

1. [Create VPC interface and S3 interface endpoints for subnets to which the worker instances will be connected](aws_create_interface_endpoints_prod.md).
2. [Create a peering connection between VPCs](aws_create_vpc_peering_connection_prod.md).
3. [Add routes to the route tables associated with the subnets of the VPCs](aws_configure_routing_network_prod.md).

1. [Create a resource share to share the subnets with other AWS accounts](aws_resource_share.md).

1. [In each production account, create security groups that will be associated with worker instances connected to the shared subnets](aws_seciruty_groups_workers.md).

[![Private Networks](images/aws_private_networks_shared_vpc.webp)](images/aws_private_networks_shared_vpc.webp "Private Networks")

Page updated 2026-07-15

