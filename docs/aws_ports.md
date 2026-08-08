---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_ports.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Ports


As Veeam Plug-in for AWS is installed on the same machine where Veeam Backup & Replication runs, it uses the same ports as those described in section [Ports](used_ports.md) —  in addition to the ports listed in the following table.

Ports

| From | To | Protocol | Port | Notes |
| Web browser (local machine) | Backup appliance | TCP/HTTPS | 443 | Required to access the Web UI component from a user workstation. |
| SSH | 22 | [Optional] Required to connect to the backup appliance using SSH. |
| TCP/HTTPS | 11005 | [Optional] Default port required to communicate with the public REST API service running on the backup appliance. For more information on Veeam Plug-in for AWS REST API, see the [Veeam Plug-in for AWS REST API Reference](https://helpcenter.veeam.com/references/vbaws/10/rest/1.9-rev0/tag/SectionAbout).  To learn how to change the port number, see the [Configuring Security Settings](https://helpcenter.veeam.com/references/vbaws/10/rest/1.8-rev0/tag/SectionOverview#section/Configuring-Security-Settings) section in the Veeam Plug-in for AWS REST API Reference. |
| Worker instances | TCP/HTTPS | 443 | Required to access the file-level recovery browser running on a worker instance during the file-level recovery process. |
| Backup appliance | SMTP server | TCP/SMTP | 25 | Default port used for sending email notifications. |
| Veeam Update Repository (repository.veeam.com), [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) (cloudfront.net, amazonaws.com) | TCP/HTTPS | 443 | Required to download available product updates, worker deployment packages and restore utilities.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |
| Ubuntu Security Repository and OS Update Repository (security.ubuntu.com, archive.ubuntu.com) | TCP/HTTP | 80 | Required to get OS security updates. |
| Microsoft Package Repository (packages.microsoft.com, dotnetcli.blob.core.windows.net) | TCP/HTTPS | 443 | Required to get .NET package updates. |
| PostgreSQL Apt Repository (apt.postgresql.org, archive.ubuntu.com) | TCP/HTTPS | 443 | Required to get PostgreSQL updates. |
| PostgreSQL Website (postgresql.org) | TCP/HTTPS | 443 | Required to download the [PostgreSQL Apt Repository key](https://www.postgresql.org/media/keys/ACCC4CF8.asc). |
| [AWS services](aws_system_requirements_aws_services.md) | TCP/HTTPS | 443 | Required to perform data protection and disaster recovery operations. |
| [Route 53 Resolver](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-dns.html#AmazonDNS) | UDP | 53 | [Optional] Default port required to perform DNS resolution if you plan to use a custom DNS server for your VPC. |
| Worker instances | [AWS services](aws_system_requirements_aws_services.md#workers) | TCP/HTTPS | 443 | Required to perform data protection and disaster recovery operations. |
| [Route 53 Resolver](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-dns.html#AmazonDNS) | UDP | 53 | [Optional] Default port required to perform DNS resolution if you plan to use a custom DNS server for your VPC. |
| Veeam Plug-in for AWS | Backup appliance, [AWS services](aws_system_requirements_aws_services.md#plug-in) | TCP/HTTPS | 443 | Port used for communication with AWS and the backup appliance. |
| AWS CheckIP service (DNS name: checkip.amazonaws.com) | TCP/HTTPS | 443 | Required to get the public IP address of the Veeam Backup & Replication server during the deployment of Veeam Plug-in for AWS. |
| Veeam Backup & Replication console and Veeam ONE server | Veeam Plug-in for AWS | TCP/HTTPS | 443 | Port used to connect to Veeam Plug-in for AWS. |

To open network ports, you must add rules to security groups associated with solution architecture components:

* A security group associated with the backup appliance. For more information, see [Deploying Appliance from Console](aws_deploy_network_resources.md).
* Security groups associated with worker instances. For more information, see [Managing Worker Configurations](aws_worker_settings.md).

To learn how to add security groups rules, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/security-group-rules.html).

Page updated 2026-05-21

