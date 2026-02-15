# EFS (Elastic File System)
## What is EFS?
```
-EFS is a file storage service for EC2.
-Multiple EC2 instances (even across AZ) can access the same files.
-Uses NFS(Network File System) protocol (port 2049).
-Automatically grows and shrinks.
-Ideal for shared access workloads.
-Fully managed and scalable.
-Can be created as Regional or One Zone.
-Supported only by Linux OS.
-For Windows → Use Amazon FSx.
```
![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/308188f7e959c51c06909f4e649eb06a43ce3f82/efs-ec2-how-it-works.png)

## Process of EFS Setup (Based on Imag
Multiple EC2 instances in different AZs use the same EFS storage.
```
Step 1: Create VPC and Subnets
 -Create a VPC.
 -Create subnets in different Availability Zones (AZ1, AZ2, AZ3.

Step 2: Launch EC2 Instances
- Launch EC2 in AZ1 subnet.
- Launch EC2 in AZ2 subnet.
- Launch EC2 in AZ3 subnet.

Step 3: Create EFS File System
- Go to EFS service.
- Click Create File System.
- Select the same VPC.

Step 4: Create Mount Targets
- Create one mount target in each AZ.
- Each mount target gets a private IP.
- Attach security group allowing NFS (Port 2049).

Step 5: Configure Security Group
 - Allow inbound rule:
   - Type: NFS
   - Port: 2049
   - Source: EC2 security group
   
Step 6: Connect EC2 to EFS
On each EC2:
→ sudo su -
→ yum install amazon-efs-utils -y
→ mkdir /efs

Mount EFS:
→ mount -t efs fs-xxxx:/ /efs

Step 7: Test Shared Storage
→ On EC2 in AZ1
→ cd /efs
→ touch demo.txt

Login to EC2 in AZ2 or AZ3:
→ cd /efs
→ ls
```
You will see the same file ✅
```
Final Flow of image
EC2 (AZ1) → Mount Target (AZ1)
EC2 (AZ2) → Mount Target (AZ2)
EC2 (AZ3) → Mount Target (AZ3)
All → Connected to One EFS File System
```
