# About this Hands-on Lab

- [ ] In this AWS hands-on lab, we will write a Lambda function that will create an EC2 instance. This Lambda function will be written in Python using the Boto3 library. We will also create a custom Lambda execution policy for our IAM role. When we’re done, we will be able to log in to the new EC2 instance via SSH.

# Learning Objectives
- [ ] Successfully complete this lab by achieving the following learning objectives:

# Create an EC2 Key Pair

- [ ] Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.
- [ ] In the navigation pane, under NETWORK & SECURITY, choose Key Pairs.

**Note:**
- [ ] The navigation pane is on the left side of the Amazon EC2 console. If you do not see the pane, it might be minimized; choose the arrow to expand the pane.
- [ ] Choose Create Key Pair.
- [ ] Enter a name for the new key pair in the Key pair name field of the Create Key Pair dialog box, and then choose Create.
- [ ] The private key file is automatically downloaded by your browser. The base file name is the name you specified as the name of your key pair, and the file name extension is .pem. Save the private key file in a safe place.
**Important:** This is the only chance for you to save the private key file. You’ll need to provide the name of your key pair when you launch an instance and the corresponding private key each time you connect to the instance.

- [ ] If you will use an SSH client on a Mac or Linux computer to connect to your Linux instance, use the following command to set the permissions of your private key file so that only you can read it.

|chmod 400 my-key-pair.pem|
|--------------------------|

- [ ] If you do not set these permissions, you cannot connect to your instance using this key pair.

# Create a Lambda Function
- [ ] Navigate to Lambda.
- [ ] Click Create a function.
- [ ] Choose Author from scratch and use the following settings:
      - Name: CreateEC2
      - Runtime: Python 3.7 or latest
      - Role: Create a custom role
- [ ] Expand Choose or create an execution role.
- [ ] Set Execution role to Create a new role with basic Lambda permissions.
- [ ] Copy the execution role name that appears.
- [ ] Click Create function.
- [ ] Navigate to IAM.
- [ ] Search for and select your newly created role.
- [ ] Edit the policy to replace its existing policy with this [file on GitHub](https://github.com/ntrao/lambda/blob/main/execution%20role.json).
- [ ] Back in the Lambda console, scroll to the Function code section and paste in the Python source code from this [file on GitHub](https://github.com/ntrao/lambda/blob/main/lambda_function_ec2_creation.py).
- [ ] Set four environment variables:
      - AMI: The ami- value of an Amazon Linux 2 instance
      - INSTANCE_TYPE: t2.micro
      - KEY_NAME: The name of your EC2 key pair
      - SUBNET_ID: The ID of one of the public subnets in your VPC
- [ ] Save the Lambda function.

# Test Lambda Function
- [ ] Click Test.
- [ ] Define an empty test event. Its contents can simply be {}.
- [ ] Give it any name you like.
- [ ] Click Create.
- [ ] Click Test again for a second test.
- [ ] Observe that an EC2 instance is initializing.

# Connect to the Newly Created EC2 Instance via SSH
- [ ] From the command line, using the .pem file you downloaded earlier, connect via the public IP of the EC2 instance.

**For example:**

|ssh -i mykeypair.pem ec2-user@IP ADDRESS |
|-------------------------------------------|
- [ ] Remember to replace <IP ADDRESS> with the public IP of the EC2 instance you created.
