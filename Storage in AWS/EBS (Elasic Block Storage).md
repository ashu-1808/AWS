
# EBS (Elastic Block Store)

## EC2 Storage Options
  ```
  1.Instance Store (Temporary storage)
  2.EBS (Persistent storage)
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
 -Snapshot 1 → A B C D E   (Full)
 -Snapshot 2 → Only changed blocks (e.g., C D)
 -Snapshot 3 → Only new changes (e.g., E)

Important Points
- Any data written after snapshot starts → Not included.
- Volumes are Availability Zone specific.
- Snapshots are Region specific.
- Snapshot can be used to create a new volume.
- Snapshot can be copied to another region.

Limits (Default)
- Up to -5000 EBS volumes- per account.
- Up to -10,000 snapshots- per region.
```
## EBS Snapshot Creation –

![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/f898c23ea9822512b67c9a5eb74a1f2e88f9de51/download.png)
Important (As shown in image)
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

