
# EBS (Elastic Block Store)

EC2 Storage Options:
```
1.Instance Store – Temporary (ephemeral) storage physically attached to the host machine.
      Data is lost when the instance is stopped or terminated.
2.EBS (Elastic Block Store) – Persistent block storage.
     Data remains even after the instance is stopped or terminated (if not deleted manually).
```
## What is EBS?
```
-EBS is a persistent block storage used with EC2.
-Think of it as a virtual hard disk attached to EC2.
-Data is not deleted when instance is stopped or rebooted.
-Network-attached storage.
```
## EBS volume types
![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/6370cb53b7f41d6a7f9b0a06679fcce2554971ca/Amazon%20EBS%20volume%20types%20flowchart.png)

![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/6370cb53b7f41d6a7f9b0a06679fcce2554971ca/EBS_Volume_Types.png)



#  Create EBS → Attach to EC2-A → Add Data → Detach → Attach to EC2-B → Verify Data

```
Step 1. Create EBS Volume
Go to AWS Console → EC2 → Volumes
 -Click Create Volume
 -Type: gp3
 -Size: 12 GiB
 -Select Same Availability Zone as EC2-A
 -Click Create Volume

Step 2. Attach EBS to EC2-A
 -Select Volume
 -Click Actions → Attach Volume
  Choose EC2-A
 -Device name:
  /dev/sdf
 -Click Attach

Step 3. Login to EC2-A
 -Check Disk
  lsblk
 -Create Filesystem
  sudo mkfs -t ext4 /dev/xvdf
 -Create Directory
  sudo mkdir /data
 -Mount Volume
  sudo mount /dev/xvdf /data
 -Add Data
  cd /data
  sudo echo "Hello from EC2-A" > test.txt
  cat test.txt

Step 4. Detach Volume from EC2-A
 -Unmount
   sudo umount /data
 -Go to Console → Volumes
 -Click Detach Volume
   Wait until status = Available

Step 5. Attach to EC2-B
 -Select Volume
 -Click Attach Volume
   Choose EC2-B
 -Device name:
   /dev/sdf
 -Click Attach

step 6. Login to EC2-B
  -Check Disk
   lsblk
⚠ Do NOT format again
  -Create Directory:
   sudo mkdir /data
  -Mount:
   sudo mount /dev/xvdf /data
  -Verify Data:
   cd /data
   ls
   cat test.txt
  -Output:
   Hello from EC2-A

✅ Data successfully transferred between EC2 instances.

---

🔥 Important Interview Points
  1. EBS is **AZ specific**
  2. Cannot attach same EBS to 2 instances at same time (except Multi-Attach for io1/io2)
  3. Always unmount before detaching
  4. Never format volume again on second instance
  5. EBS is persistent storage


🎯 Real-Time Use Case
  1. Moving application data between servers
  2. Migrating data to new EC2 instance
  3. Backup and restore operations
  4. Disaster recovery testing
```


## EBS Snapshot Creation –
![image alt](https://github.com/ashu-1808/AWS/blob/f898c23ea9822512b67c9a5eb74a1f2e88f9de51/download.png)

## EBS Snapshot :
```
What is EBS Snapshot?
- EBS Snapshot is a point-in-time backup of an EBS volume.
- It is an incremental data backup.
- Snapshots are stored in AWS (S3 managed storage).

How Snapshot Works
- First snapshot → Full backup (copies all data).
- Next snapshots → Copies only changed blocks since last snapshot.
- Saves storage space and cost.

Example:
 -Original Volume → A B C D E
 -Snapshot 1 → A B   (Full)
 -Snapshot 2 → Only changed blocks (e.g., C D)
 -Snapshot 3 → Only new changes (e.g., E)

Important Points
- Any data written after snapshot starts → Not included.
- Volumes are Availability Zone specific.
- Snapshots are Region specific.
- Snapshot can be used to create a new volume.
- Snapshot can be copied to another region.
- EBS Snapshot Quotas (Default Limits)
   1.Total Snapshots: Up to 100,000 per region.
   2.Concurrent Copies: Maximum 20 per destination region.
   3.Concurrent Restores: 5 per account.
   4.Archived Snapshots: 25 per volume.
```

### Important (As shown in image)
```
- First snapshot → Full backup
- Next snapshots → Only changed blocks
- Snapshot = Point-in-time backup
- Stored in AWS (S3 managed storage)
- Incremental → Saves storage cost
```
## Steps to Create EBS Snapshot
```
1. Go to AWS Management Console

2. Navigate to EC2 Dashboard

3. Click on Volumes

4. Select the volume you want to backup

5. Click Actions → Create Snapshot

6. Provide Description

7. (Optional) Select Encryption / KMS key

8. Click Create Snapshot

 After Creation
  - Go to Snapshots section
  - Status will show Pending → Completed
```

## EBS migration:
```
- Volumes are Availability Zone specific.
- Snapshots are Region specific.
- Snapshot is required to move volume across regions.
- Data remains intact during migration.
```
 Process Flow (Simple Diagram Format)
```
EBS Volume (Mumbai)
        ↓
Create Snapshot
        ↓
Copy Snapshot to Hyderabad
        ↓
Create Volume from Snapshot
        ↓
Attach to EC2 (Hyderabad)
```

![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/f898c23ea9822512b67c9a5eb74a1f2e88f9de51/download%20(1).png)
## EBS Migration – Moving EBS Volume from One Region to Another:
```
To move EBS from one AZ/Region:
1. Create snapshot of volume.
2. Copy snapshot (if moving to another region).
3. Create new EBS volume from snapshot.
4. Attach to EC2 instance.
```
Steps:
```
📍 Source Region (Example: Mumbai)
1. Attach extra EBS volume to instance (if needed).
2. Create Snapshot of the EBS volume.

🌍 Copy Snapshot to Destination Region
3.Select the snapshot.
4. Click Actions → Copy Snapshot
5. Choose Destination Region (Example: Hyderabad).
6. Initiate copy snapshot.
7. Wait for status → Pending → Completed.

📍 Destination Region (Example: Hyderabad)
8 Go to destination region.
9. Open Snapshots section.
10. Select copied snapshot.
11. Click Create Volume from Snapshot.
12. Choose correct Availability Zone (AZ).
13. Create volume.
14.Attach volume to EC2 instance.

```

