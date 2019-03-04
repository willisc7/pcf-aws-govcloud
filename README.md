# Pivotal Cloud Foundry on AWS GovCloud
**Instructions to deploy Pivotal Cloud Foundry on AWS GovCloud**

PreReqs:
- AWS Commercial and AWS GovCloud accounts with admin privileges
---

## Launch a jumpbox ##
1. Create a VPC
2. Create a subnet (e.g. 192.168.0.0/24)
3. Create an IGW and attach it to the VPC
4. Edit the route table to allow 0.0.0.0/0 to the IGW
5. Launch a Ubuntu instance and create a new key pair
6. Create new elastic IP allocation and associate it with instance
7. ssh -i /path/my-key-pair.pem ubuntu@52.222.60.130

## Identify AMI IDs for Ubuntu Stemcell & Ops Manager
1. Review the [release notes](https://docs.pivotal.io/pivotalcf/pcf-release-notes/) to determine which stemcell version is compaitible with which ops man version

```
For example, `Ops Manager 2.3.11` is compatible with `Stemcell 97.57`
```

2. Search https://network.pivotal.io for those versions and download the AWS release files.

```
https://network.pivotal.io/products/ops-manager/
https://network.pivotal.io/products/stemcells-ubuntu-xenial
```

3. Review the manifest file in the release file download and determine AMIs

```
Ops Manager 2.3-build.258 (us-gov-west-1) = ami-d7bad2b6
Ubuntu Stemcell 97.57 (us-gov-west-1) = ami-d3f997b2
```

## Launch AMIs
Launch the Ops Manager AMI `ami-10f67271` and proceed with standard PCF installation. :clap:

