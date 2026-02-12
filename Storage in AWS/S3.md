
#  Amazon S3

##  What is S3?
```
1 S3 is region-specific
2 Used to store and retrieve unlimited data
3 It is object-based storage
- ❌ Cannot install OS on S3
- Data stored in minimum 3 AZs in same region
- Very high durability (11 9’s)
- Buckets in S3
   1. Bucket is a container for objects
   2. Bucket structure is flat
   3. ❌ No nested buckets (no bucket inside bucket)
   4. Bucket name must be globally unique  
-S3 Object Size
   1. Minimum → 0 bytes
   2. Maximum → 5 TB
-S3 Bucket Limits
   1. Default → 100 buckets per account
   2. Can request increase from AWS
-S3 Bucket Name Rules
   1. Must be globally unique
   2. No duplicate bucket names in AWS
-S3 Bucket Access Methods
   1.ACL (Access Control List)
    a. Used for basic permissions
    b. Controls access at:Bucket level
                      Object level
-S3 Bucket Policy
   1. Must delete all objects before deleting bucket
   2. JSON-based
   3. Used for detailed permissions
   4. Applied at bucket level

```


## Amazon S3 Properties 
```
1) Bucket Versioning
  - Keeps multiple versions of the same object.
  - Helps recover files that are accidentally deleted or overwritten.
  - Must be enabled on the bucket.

2) Encryption
  A) Server-Side Encryption (SSE)
    - S3 encrypts data**before storing it.
    - S3 decrypts data when you download it.
    - All new S3 objects are encrypted by default.
    - Types:
     1. SSE-S3 (Default:
       - Uses AES-256 encryption.
       - Managed completely by AWS.
     2. SSE-KMS:
       - Uses AWS Key Management Service (KMS).
       - Gives more control over encryption keys.
       - Can use AWS managed key or customer managed key.
     3. DSSE-KMS (Double Encryption:
       - Applies two layers of encryption
       - Used for high security and compliance needs.
  B) Client-Side Encryption
    - You encrypt data before uploading to S3.
    - You manage: Encryption keys, Encryption tools, Entire encryption process
       
3) Transfer Acceleration
  - Speeds up upload and download of data to/from S3.
  - Uses AWS global edge network.
  - ⚠️ Extra cost applies.

4) Requester Pays
 - Normally, **bucket owner pays for storage and data transfer.
 - The person downloading data pays for download cost.
 - Bucket owner still pays for storage.
 - Useful when sharing large datasets.
 -Example:Public data, Reference data, Geographic data.


5) Object Lock
- Uses WORM (Write Once Read Many model.
- Prevents objects from being: Deleted, Overwritten
- Can lock for: Fixed time, Indefinitely
- Works only with versioning enabled buckets.

6) Static Website Hosting
- S3 can host static websites.
- Supports: HTML, CSS, JavaScript
- ❌ Not support server-side scripting like: PHP, JSP, ASP.NET
   For dynamic websites, use: EC2, Elastic Beanstalk, Lambda
```


## Amazon S3 storage class:
![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/e7cf2f64449efbdfff60d1468816ef30d1859d9f/storage%20class.webp)




##  S3 Replication
```
1. Same Region Replication (SRR)
- Copies objects from one bucket to another bucket in the same AWS region
- Used for: Data redundancy, Log aggregation, Compliance requirements
- Example: Mumbai bucket → another Mumbai bucket

2. Cross Region Replication (CRR)
- Copies objects from one bucket to another bucket **in a different AWS region**
- Used for: Disaster recovery, High availability, Global access.
- Example:Mumbai bucket → Hyderabad bucket
```

##  EC2 to S3 (Upload & Download Process):
This is used when you want to transfer files between an EC2 instance and an S3 bucket.
```
Step 1: Create Resources
  a. Create a Linux EC2 instance
  b. Create an S3 bucket
  c.Give permission (S3 Full Access Create an IAM Role)   
  d. Attach the IAM role to the EC2 instance
  (IAM role allows EC2 to access S3 without access keys.)

Step 2: Connect to EC2
Login to your instance:
 → sudo su -

Step 3: Check S3 Buckets
 → aws s3 ls
(Shows list of available S3 buckets.)

Step 4: Create a File in EC2
 → touch file1.txt
 (Creates a file inside EC2.)

Step 5: Upload File to S3
 → aws s3 mv file1.txt s3://bucket_name
 (Moves (uploads) file from EC2 to S3 bucket.)

Step 6: Download File from S3
 → aws s3 cp s3://bucket_name/file1.txt .
(Copies file from S3 bucket to EC2.)

```
```
 In Simple Words
- EC2 = Server
- S3 = Storage
- IAM Role = Permission bridge between EC2 and S3
- `mv` = Upload
- `cp` = Download
```



