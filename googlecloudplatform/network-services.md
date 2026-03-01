# Google Network Services

Google cloud provides different cloud network services that allow you to create and manage public & private networks. 1 of the most important service is Cloud VPC.

## Cloud VPC
A Virtual Private Cloud is a network that is secure & isolated in cloud. Google Cloud allows to create and configure it easily with a couple button clicks or a simple command.

<!-- TODO: Create Cloud VPC gcloud cli command -->

A VPC is a very important piece without which you cannot create most of resources, from ComputeEngine VMs to Cloud Storage and Pubsub instances require a VPC network & subnet to work.

When you create a Google Cloud project a default VPC is created by default and it has 1 subnet in every region available in Google Cloud Network Locations.

VPC is a global resource which hosts multiple subnets with different IP range blocks for different regions. These IP blocks are represented using CIDR notation. A Subnet is a region resource representing a network in the VPC.

> **CIDR**
> CIDR - Classless Inter-Domain Routing
> CIDR block expresses a range of IP addresses using a starting IP and a range value.
> e.g. 198.10.0.0 / 28 ==> this shows starting from 198.10.0.0 to 198.10.0.15.
> IP / Range - IP is the starting IP and Range is the number of fixed bits in the binary notation of the IP.

### Best Practices


## Cloud FireWall
## Connecting VPC with other VPCs
## Connecting VPC with On-prem
## Cloud DNS
