# Automated PCF Lite Installation on AWS GovCloud

## Prerequisites
- AWS GovCloud account with admin privileges
- Download and install [Terraform](https://www.terraform.io/downloads.html)
---

## Launch a Jumpbox
1. Create a VPC
2. Create a subnet (e.g. 192.168.0.0/24)
3. Create an IGW and attach it to the VPC
4. Edit the route table to allow 0.0.0.0/0 to the IGW
5. Launch a Ubuntu instance and create a new key pair
6. Create new elastic IP allocation and associate it with instance
7. ssh -i /path/my-key-pair.pem ubuntu@52.222.60.130

## Identify AMI IDs for Ubuntu Stemcell & Ops Manager
1. Review the [release notes](https://docs.pivotal.io/pivotalcf/pcf-release-notes/) to determine which stemcell version is compaitible with which ops man version. For example, Ops Manager 2.3.11 is compatible with Stemcell 97.57
2. Download the AWS release files for [Ops Manager](https://network.pivotal.io/products/ops-manager/) and [BOSH Stemcell](https://network.pivotal.io/products/stemcells-ubuntu-xenial)
3. Open the .MF file for each and copy the AMI for the appropriate AWS region you're operating in (e.g. us-gov-west-1)

## Configure PCF AWS Terraform Templates
Follow the directions [here](https://docs.pivotal.io/pivotalcf/om/aws/prepare-env-terraform.html) to download the latest PCF AWS Terraform Templates and configure them appropriately. Replace the **workspace/pivotal-cf-terraforming-aws-7e09091** directory in this repository with the updated version you just downloaded.