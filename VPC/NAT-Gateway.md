# NAT-Gateway

## What is NAT Gateway?

  A NAT (Network Address Translation) Gateway allows instances in a private subnet to access     the internet.
  But prevents the internet from initiating a connection with those instances.
  It provides outbound internet access only.
Why Do We Need NAT Gateway?
 - Private subnet instances do not have public IP
 - They cannot access internet directly
 - NAT Gateway enables: - Software updates
                      - Downloading packages
                      - Accessing external APIs
 - But keeps them secure (no inbound internet access)



How NAT Gateway Works (Flow)
 `Private EC2 → Route Table → NAT Gateway → Internet Gateway → Internet`


Important Points (Interview Ready)
 - NAT Gateway works only in public subnet
 - Requires Elastic IP
 - Only allows outbound traffic
 - Highly available within an Availability Zone
 - Managed service (no maintenance required)

## Steps to Create NAT Gateway

![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/27374f3cb63a2fafd2943137b00f62e35e5cc34e/VPC/NAT-gateway.png)

```
Step 1 [Create VPC]
1. If you don’t already have a VPC, you can create one by clicking “Create VPC" in the VPC dashboard
2. Click the “Create VPC” button
3. Fill in the VPC details including name, IPv4 CIDR block and any other settings you require
   Use 10.0.0.0/16 CIDR for VPC**
4. Click Create VPC

Step 2 [Create Subnet]
1. In the VPC dashboard select Subnets from the left hand navigation pane
2. Click the create subnet button
3. Choose the VPC you created in previous step
4. Configure the subnet details including the name, Availability zone and IPv4 CIDR block
5. For public subnet give 10.0.0.0/24 CIDR and for private subnet give 10.0.1.0/24 CIDR
6. Repeat the process and create both public and private subnet

Step 3 [Create Internet Gateway]
1. In the VPC dashboard select Internet gateway from left hand side of navigation pane
2. Click the create internet gateway button

Step 4 [Create Custom Route Table]
1. In the VPC dashboard select Route table from left side navigation pane
2. Click the create route table button
3. provide aname to publicsubnet and private subnetand choose the vpc you
   want to associate withnew route table
4. click create

Step 5 [Attach the IGW to your VPC]
1. Select the newly created Internet gateway
2. Click the “Actions”button and choose Attach to VPC
3. Choose the VPC you want to connect Internet gateway
4. Click attach

Step 6 [Edit the route table to route traffic to the internet]
1. Select the newly created custom route table
2. In the routes tab click the edit route button
3. Click add route
4. In the destination field enter 0.0.0.0/0 to represent all internet bound traffic
5. In the target field select the Internet gateway that you attached the VPC in previous steps
6. Click save routes

Step 7 [Associate subnets with custom route table]
1. In the subnet Associations tab of the custom route table click **edit subnet associations**
2. Choose the subnet that you want to associate with this custom route table. Typically this would be the public subnet and private subnets which are associated with public subnet respectively
3. Click save associations

Step 8 [Launching a windows EC2 instance]
1. Launch instance
2. Select windows server AMI
3. Set the instance type
4. Provide a name Public-subnet and Private-subnet
5. Choose the VPC you want to associate with new instance
6. Click create

Step 9 [Choose an existing keypair or create new keypair]
1. If you already have an EC2 keypair select it
2. If not create a new keypair, select it and securely connect to your windows EC2 instance
3. Save file on your local device (Make sure it is safe)

Step 10 [Configure the Security group & Virtual Private Cloud]
1. Automatically assigned Public IP should be disabled for private subnet and vice-versa
2. Create a new security group or select an existing one. Define rules to allow
   RDP port 3389
3. Click on Launch to proceed

Step 11 [Connect your EC2 instance]
1. In the RDP client tab click on Download Remote Desktop File on your local machine
2. Click on get password and upload the private key
3. Click on decrypt password and copy decrypted password
4. Open the RDP file and paste your copied decrypted password
5. You are successfully connected to your windows EC2 server (You can find it in windows under “Remote Desktop Connection”)
6. Repeat the process for private instance
7. In the computers field enter the private IP address of your EC2 instance
8. Click connect
9. If prompted enter the username and password for your windows EC2 instance. The user name is typically **“Administrator”**
10. Click “OK”

Step 12 [Testing Your Connectivity]
1. Open the command prompt
2. Run the command `ping 8.8.8.8 -t`
3. The reply from the ping command is successful

Step 13 [Create the NAT Gateway]
1. In the “Create NAT Gateway” wizard select the public subnet where you want to create NAT gateway
2. Choose an elastic IP address to associate with the NAT gateway. If you don’t have one, you can allocate a new Elastic IP
3. Click the create NAT Gateway button


Step 14 [Add a Route to the NAT Gateway]

1. In the route table click the edit route button
2. Add a new route with the destination as **0.0.0.0/0** (All internet bound traffic) and select NAT-Gateway as target
3. Click “Save Routes”

tep 15 [Testing your connectivity]

1. Open the command prompt
2. Run the command `ping 8.8.8.8 -t`
3. Reply from the ping command is successful
```
