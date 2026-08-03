---
title: "Step 3. Specify Network Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_worker_configuration_network.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Network Settings


At the Network step of the wizard, select an Amazon VPC network and a subnet to which you want to connect worker instances, and specify a security group that must be associated with the instances. For an Amazon VPC network, a subnet and a security group to be displayed in the lists of available network specifications, they must be created in AWS as described in [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html).

The backup appliance will apply the specified network settings to all worker instances that will be deployed in the AWS Region and Availability Zone selected at the General step of the wizard.

|  |
| --- |
| Important |
| * Security rules configured in the selected security group must allow direct network traffic required to communicate with [AWS services](aws_system_requirements_aws_services.md). To learn how to add rules to security groups, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html#AddRemoveRules). * Proxy redirect and setting a proxy in the backup appliance configuration are not supported. |

By default, the backup appliance uses public access to communicate with worker instances. That is why the public IPv4 addressing attribute must be enabled for the selected subnet, the selected VPC network must have an internet gateway attached, and the VPC network and subnet route tables must have routes that direct internet-bound traffic to this internet gateway. If you want worker instances to operate in a private network, do either of the following:

* Enable the private network deployment functionality, and configure specific VPC endpoints for the subnet to let the backup appliance use private IPv4 addresses as described in section [Configuring Private Network Deployment](aws_enable_private_network_deployment.md).

For the list of specific endpoints required to perform backup and restore operations, see [Configuring Private Networks](aws_configuring_private_networks.md).

* Configure VPC endpoints as described in section [Appendix C. Configuring Endpoints in AWS](aws_configure_endpoints.md).

[![Adding Worker Configuration](images/aws_worker_config_networks.webp)](images/aws_worker_config_networks.webp "Adding Worker Configuration")

Page updated 2026-05-20

