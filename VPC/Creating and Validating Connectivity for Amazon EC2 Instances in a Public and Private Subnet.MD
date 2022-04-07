# About this Hands-on Lab

- [ ] AWS networking consists of multiple components, and understanding the relationship between the networking components is a key part of understanding the overall functionality and capabilities of AWS. In this hands-on lab, we will create a VPC with an internet gateway, as well as create subnets across multiple Availability Zones.

# Learning Objectives

Successfully complete this lab by achieving the following learning objectives:

# Create an Internet Gateway, and Connect It to the VPC

Create an internet gateway, and attach it to the VPC1 VPC.

# Create a VPC

Create a VPC from scratch (without using the VPC Wizard).
Name the VPC VPC1
Set the VPC CIDR to 172.16.0.0/16.
Create a Public and Private Subnet in Different Availability Zones
Create a public and private subnet in different Availability Zones using the following IP CIDR addresses:

Public1 subnet in us-east-1a: 172.16.1.0/24
Private1 subnet in us-east-1b: 172.16.2.0/24
Create Two Route Tables, and Associate Them with the Correct Subnet
Note: The VPC has a default route table, but we will be creating custom route tables.

Create two route tables:
One for the public subnet named PublicRT with an internet gateway route
One for the private subnet named PrivateRT without an internet gateway route
For the public route table, create a default route to the internet using the 0.0.0.0/0 CIDR notation.
Create Two Network Access Control Lists (NACLs), and Associate Each with the Proper Subnet
Create a public NACL named Public_NACLwith inbound rules allowing HTTP and SSH traffic, as well as an outbound rule allowing TCP traffic on port range 1024-65535.

Associate the public NACL with the public subnet.

Create a private NACL named Private_NACLwith an inbound rule allowing SSH traffic with a source of 172.16.1.0/24, as well as an outbound rule allowing TCP traffic on port range 1024-65535.

Associate the private NACL with the private subnet.

https://acloudguru.com/hands-on-labs/create-a-basic-vpc-and-associated-components-in-aws
