---
title: "Step 1. Create Interface Endpoints"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_create_interface_endpoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 1. Create Interface Endpoints


To allow backup appliances to create EC2 and RDS image-level backups, to perform restore operations and to save EFS indexes to backup repositories, you must configure specific VPC interface endpoints for all subnets to which worker instances deployed for these operations will be connected. For the list of VPC interface endpoints required for backup and restore operations, see [Configuring Private Networks](aws_configuring_private_networks.md#worker_operations).

|  |
| --- |
| Note |
| For backup appliances to be able to deploy worker instances based on VPC networks and subnets for which you create VPC interface endpoints, you will have to add the necessary worker configurations as described in section [Managing Worker Configurations](aws_worker_settings.md). If you do not add specific worker configurations, backup appliances will use either the default or the [most appropriate network settings](aws_workers_location.md) of AWS Regions. |

Creating Interface Endpoints

To create an interface VPC endpoint, do the following:

1. Log in to the AWS Management Console using credentials of an AWS account in which you want to create the endpoint.
2. Navigate to Services > Networking & Content Delivery and click VPC.
3. In the Amazon VPC console, navigate to Virtual Private Cloud > Endpoints and click Create Endpoint.
4. Complete the Create endpoint wizard:

1. At the Endpoint settings step, do the following:

1. [Optional] In the Name tag field, specify a name for the endpoint.
2. In the Service category section, select the AWS services option.

1. At the Services step, enter Interface in the search field, and choose a service for which you want to create the endpoint.
2. At the VPC step, do the following:

1. From the VPC drop-down list, choose a VPC to which the deployed worker instances will be connected. Make sure that the Enable DNS hostnames check box is selected for the VPC.
2. In the Additional settings section, select the Enable DNS name check box.

1. At the Subnets step, choose a subnet for each Availability Zone where the worker instances will be deployed, and specify the IP address type. Make sure that the Auto-assign public IPv4 address check box is not selected for the subnet.
2. At the Security groups step, choose security groups that will be associated with the endpoint network interface.

Ensure that each security group allows communication between the associated endpoint network interface and the resources in your VPC communicating with the selected service. If a security group restricts inbound HTTPS traffic (port 443) from the resources in the VPC, you will not be able to send traffic through the endpoint network interface.

1. At the Policy step, select the Full access option to allow full access to the service. Alternatively, select the Custom option, and attach a VPC endpoint policy that will control permissions required to access available resources over the VPC endpoint.
2. Click Create Endpoint.

For more information on interface VPC endpoints, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html?ad=in-text-link#create-interface-endpoint).

Creating S3 Interface Endpoints

To create an S3 interface VPC endpoint, do the following:

1. In the Amazon VPC console, navigate to Virtual Private Cloud > Endpoints and click Create Endpoint.
2. Complete the Create endpoint wizard:

1. At the Endpoint settings step, do the following:

1. [Optional] In the Name tag field, specify a name for the endpoint.
2. In the Service category section, select the AWS services option.

1. At the Services step, enter S3 in the search field and choose the com.amazonaws.<region>.s3 service with the Interface type, where <region> is the name of an AWS Region in which a backup repository is located.
2. At the VPC step, choose a VPC to which the deployed worker instances will be connected.
3. At the Subnets step, choose a subnet for each Availability Zone where the worker instances will be deployed, and specify the IP address type.
4. At the Security groups step, choose security groups that will be associated with the endpoint network interface.

1. At the Policy step, select the Full access option to allow full access to the service. Alternatively, select the Custom option, and attach a VPC endpoint policy that will control permissions required to access available resources over the VPC endpoint.

1. Click Create Endpoint.

|  |
| --- |
| Important |
| The backup appliance and worker instances must be able to communicate with the Amazon S3 service through the created S3 interface endpoint. That is why security groups associated with the endpoint network interface must allow inbound HTTPS traffic from both the backup appliance and the worker instances through port 443. |

For more information on interface endpoints for Amazon S3, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/privatelink-interface-endpoints.html).

Page updated 2026-05-19

