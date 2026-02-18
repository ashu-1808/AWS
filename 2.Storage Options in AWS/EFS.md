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

## Process of EFS Setup 


```
Step 1: Create VPC and Subnets
 - Create a VPC (Enable DNS resolution and DNS hostnames).
 - Create subnets in different Availability Zones (AZ1, AZ2, AZ3).
 - (If using public EC2) Attach an Internet Gateway and update route table.

Step 2: Configure Security Group for all EC2
 Allow inbound rule:
   - Type: SSH
   - Port: 22
   - Source: Your IP (recommended) or Anywhere (0.0.0.0/0)
 Note:
   - Do NOT allow Port 2049 in EC2 security group.

Step 3: Launch EC2 Instances
 - Launch EC2 in AZ1 subnet.
 - Launch EC2 in AZ2 subnet.
 - Launch EC2 in AZ3 subnet.
 - Attach the EC2 Security Group.

Step 4: Create EFS File System
 - Go to EFS service.
 - Click Create File System.
 - Select the same VPC.
 - Proceed with default or customized settings.
Note:
 - Amazon EFS is a regional service.

Step 5: Create Mount Targets
 - Create one mount target in each AZ.
 - Each mount target gets a private IP address.
 - Attach EFS Security Group (configured for NFS access).
 Important:
   - Mount targets are Availability Zone specific.

Step 6: Configure Security Group for EFS
 Allow inbound rule:
   - Type: NFS
   - Port: 2049
   - Source: EC2 Security Group  (NOT 0.0.0.0/0)
 Outbound:
   - Allow All (default)

Step 7: Connect EC2 to EFS
 -On each EC2:
  → sudo yum install amazon-efs-utils -y
  → sudo mkdir /efs
 -Mount EFS (Copy the DNS mount helper command from EFS console):
  → sudo mount -t efs fs-xxxx:/ /efs
 (Repeat the same mount command on all EC2 instances.)

Step 8: Test Shared Storage
 → On EC2 in AZ1
 → cd /efs
 → touch demo.txt
- If permission denied:
 → sudo chown ec2-user:ec2-user /efs
-Login to EC2 in AZ2 or AZ3:
 → cd /efs
 → ls


You will see the same file ✅

Final Flow of Architecture
  EC2 (AZ1) → Mount Target (AZ1)
  EC2 (AZ2) → Mount Target (AZ2)
  EC2 (AZ3) → Mount Target (AZ3)
All EC2 Instances → Connected to One Amazon EFS File System



# Key Technical Points
  1. Amazon EFS is a regional service.
  2. Mount targets are Availability Zone specific.
  3. EFS uses NFS version 4.1.
  4. Port used: 2049.
  5. Multiple EC2 instances across AZs can access the same file system simultaneously.
```

