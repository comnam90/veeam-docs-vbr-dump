---
title: "Appendix C. Configuring Endpoints in AWS"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_configure_endpoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix C. Configuring Endpoints in AWS


|  |
| --- |
| Important |
| The provided instructions on configuring endpoints are not compatible with the [private network deployment](aws_private_network_deployment.md) functionality. If you plan to use this functionality, follow the instructions provided in section [Configuring Private Networks](aws_configuring_private_networks.md). |

If you want worker instances to operate in private environments, that is to use subnets with disabled auto-assignment of Public IPv4 addresses to deploy worker instances in AWS Regions, configure specific endpoints for services used by the backup appliance to perform backup and restore operations.

The following endpoints are required to perform data protection and disaster recovery operations.

Appendix C. Configuring Endpoints in AWS

| Operation | Interface Endpoints | S3 Gateway Endpoints |
| Creating EC2 image-level backups | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs * com.amazonaws.<region>.ebs | * com.amazonaws.<region>.s3 |
| Restoring EC2 instances from image-level backups | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Restoring EC2 volumes from image-level backups | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Performing health check for EC2 backups | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Creating EC2 archived backups | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Creating RDS image-level backups | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Restoring PostgreSQL DB instances from image-level backups | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Performing health check for RDS backups | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Creating RDS archived backups | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Applying retention policy settings to created restore points | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |
| Performing file-level recovery from image-level backups | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs  * [Applies only if you [restore to the original location](aws_restore_item_mode.md#mode)] com.amazonaws.<region>.kinesis-streams | * com.amazonaws.<region>.s3 |
| Performing file-level recovery from cloud-native snapshots and replicated snapshots | * com.amazonaws.<region>.ec2messages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs * [Applies only if you [restore to the original location](aws_restore_item_mode.md#mode)] com.amazonaws.<region>.kinesis-streams | * com.amazonaws.<region>.s3 |
| Performing EFS indexing | * com.amazonaws.<region>.ssmmessages * com.amazonaws.<region>.ssm * com.amazonaws.<region>.sqs | * com.amazonaws.<region>.s3 |

To create these endpoints, use the specified endpoint names, where <region> is the name of an AWS Region in which worker instances will be deployed.

Creating Interface Endpoints

|  |
| --- |
| Note |
| This section provides instructions on steps performed in a third-party application. Keep in mind that the instructions may become outdated. For up-to-date instructions, see AWS Documentation. |

To allow backup appliances to create EC2 and RDS image-level backups and to perform restore operations and EFS indexing, configure interface VPC endpoints in AWS regions where worker instances are deployed for subnets to which worker instances must be connected. By default, backup appliances use the default or the most appropriate network settings of AWS Regions to deploy worker instances. However, you can add specific worker configurations as described in section [Configuring Private Networks](aws_configuring_private_networks.md).

For more information on AWS regions in which worker instances are deploy to perform specific operations, see [Worker Instances in Private Environment](aws_worker_instances_in_private.md).

To create an interface VPC endpoint, do the following:

1. Log in to the AWS Management Console using credentials of an AWS account in which you want to create the endpoint.
2. In the AWS services section, navigate to All Services > Networking & Content Delivery and click VPC. The VPC console will open.
3. Navigate to Virtual Private Cloud > Endpoints and click Create Endpoint. The Create endpoint wizard will open.
4. Complete the Create endpoint wizard:

1. At the Endpoint settings step of the wizard, do the following:

1. [Optional] In the Name tag field, specify a name for the endpoint.
2. In the Service category section, select AWS services.

1. At the Services step of the wizard, use the following filter Type: Interface and select a service for which you want to create a VPC endpoint.
2. At the VPC step of the wizard, do the following:

1. From the VPC drop-down list, select a VPC to which the deployed worker instances will be connected.
2. In the Additional settings section, select the Enable DNS name check box.

1. At the Subnets step of the wizard, select one subnet for each Availability Zone where worker instances will be deployed.
2. At the Security groups step of the wizard, select security groups that will be associated with the endpoint network interfaces.

Ensure that the security group that is associated with the endpoint network interface allows communication between the endpoint network interface and the resources in your VPC that communicate with the service. If the security group restricts inbound HTTPS traffic (port 443) from resources in the VPC, you will not be able to send traffic through the endpoint network interface.

1. At the Policy step of the wizard, select Full access to allow full access to the service. Alternatively, select Custom and attach a VPC endpoint policy that will control permissions on resources available over the VPC endpoint.
2. Click Create Endpoint.

For more information on interface VPC endpoints, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html?ad=in-text-link#create-interface-endpoint).

Creating S3 Gateway Endpoints

|  |
| --- |
| Note |
| This section provides instructions on steps performed in a third-party application. Keep in mind that the instructions may become outdated. For up-to-date instructions, see AWS Documentation. |

To allow backup appliances to create image-level backups of EC2 instances, to perform restore operations from these backups, and to save EFS indexes to backup repositories, configure S3 gateway endpoints in AWS regions where worker instances are deployed for subnets to which worker instances must be connected. By default, backup appliances use the default or the most appropriate network settings of AWS Regions to deploy worker instances. However, you can add specific worker configurations as described in section [Managing Worker Configurations](aws_worker_settings.md).

For more information on AWS regions in which worker instances are deployed to perform specific operations, see [Worker Instance Locations](aws_workers_location.md).

To create a gateway endpoint for a subnet, do the following:

1. Log in to the AWS Management Console using credentials of an AWS account in which you want to create the endpoint.
2. In the AWS services section, navigate to All Services > Networking & Content Delivery and click VPC. The VPC console will open.
3. Navigate to Virtual Private Cloud > Endpoints and click Create Endpoint. The Create endpoint wizard will open.
4. Complete the Create endpoint wizard:

1. At the Endpoint settings step of the wizard, do the following:

1. [Optional] In the Name tag field, specify a name for the endpoint.
2. In the Service category section, select AWS services.

1. At the Services step of the wizard, use the following filter Type: Gateway and select com.amazonaws.<region>.s3, where <region> is a name of an AWS Region in which worker instances will be deployed.
2. At the VPC step of the wizard, select a VPC to which the deployed worker instances will be connected.
3. At the Route tables step of the wizard, select the route tables to be used by the endpoint. AWS automatically will add a route that points traffic destined for the service to the endpoint network interface.
4. At the Policy step of the wizard, select Full access to allow full access to the service. Alternatively, select Custom and attach a VPC endpoint policy that will control permissions on resources available over the endpoint.
5. Click Create Endpoint.

For more information on gateway endpoints for Amazon S3, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-s3.html).

|  |
| --- |
| Important |
| When you create an S3 gateway endpoint, consider that a VPC and a service for which you create the endpoint must belong to the same AWS Region. That is, when you perform backup operations using endpoints, the processed source instances must reside in the region in which a repository where the backups will be stored is located; when you perform restore operations using endpoints, the instances must be restored to the region in which a repository where the backup files are stored is located.  This limitation is only region-specific-services and VPCs can belong to different AWS accounts. |

Page updated 2026-05-20

