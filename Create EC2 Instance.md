# About this Hands-on Lab

- Elastic Compute Cloud (EC2) is AWS’s Infrastructure as a Service product. It provides a huge range of virtual machines suitable for general purpose and specialized on-demand compute tasks. In this hands-on lab, you will gain experience creating and interacting with an EC2 instance. The lab covers EC2 requirements, the choices available with creating EC2 instances, and the provisioning process itself. By the end of the lab, you will have gained the experience needed to be confident using EC2 in smaller deployments, such as blogs or lower-volume websites.

# Learning Objectives
- Successfully complete this lab by achieving the following learning objectives:

# Create a Default VPC
1.Navigate to VPC > Your VPCs.
2.Select Actions > Create default VPC.
3.Click Create default VPC.

# Create an EC2 Instance
- Navigate to EC2 > Instances.
- Click Launch instance.
- On the AMI page, select the Amazon Linux 2 AMI.
- Leave t2.micro selected, and click Next: Configure Instance Details.
- On the Configure Instance Details page:
     - Network: default
     - Subnet: No preference
     - Auto-assign Public IP: Enable
 - Expand Advanced details, and paste the following into the user data box:
 
| Commands                                                 |
|-----------------------------------------------------------|
|#!/bin/bash                                               |
|yum update -y                                             |  
|yum install -y httpd                                      |
|yum install -y curl                                       |
|chkconfig httpd on                                        |
|service httpd start                                       |

- Click Next: Add Storage, and then click Next: Add Tags. 
- On the Add Tags page, select Add Tag then add the following:
       - Key: Name
       - Value: Webserver
- Click Next: Configure Security Group.

- On the Configure Security Group page, click Create a new security group, and set the following values:

Security group name: LabSG
Description: LabSG
Click Add Rule, and set the following values (leave the default SSH rule):

Type: HTTP
Source: My IP
Click Review and Launch, and then Launch.

In the key pair dialog, select Create a new key pair.

Give it a Key pair name of "Lab".

Click Download Key Pair, and then Launch Instances.

Click View Instances, and give it a few minutes to enter the running state.

Manage the EC2 Instance
Once the instance is running with 2/2 status checks:

Copy the instance’s public DNS (IPv4), and paste it into a new browser tab.
On the EC2 instances console, right-click the instance, and select Connect.
In the terminal, change to your downloads directory (e.g., cd Downloads).
Run chmod 400 Lab.pem to adjust the permissions on the file.
If using Windows, you will need to follow the instructions found here.
Connect to the instance using the ssh command provided in the dialog when you click Connect (or using the PuTTY instructions).
Note the IPv4 public IP of the instance.
With the instance selected, click Actions > Instance State > Reboot.
Does the IP change?
Click Actions > Instance State > Stop.
After it’s stopped, click Actions > Instance State > Start.
Does the IP change?
Click Actions > Instance State > Stop.
Once it’s stopped, click Actions > Instance Settings > Change Instance Type.
Change the instance type to t3.small, and click Apply.
