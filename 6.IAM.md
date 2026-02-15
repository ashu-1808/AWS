

# IAM (Identity and Access Management)

## IAM:
```
- IAM is a service that helps you securely control access to AWS resources.
- IAM helps you centrally manage permissions and access
- Allows you to grant permissions and access to AWS resources.
- IAM lets you manage users and access.
- You use IAM to control who is authenticated (signed in) and authorized (has permission) to use resources.

```

## IAM Features
```
A. Shared access to your AWS Account
 - IAM allows multiple users and services to use AWS account
 - Each user get separate credentials
 - No need to share root password
 - Why it matters :
  1. Root account remains highly secure
  2. Easy collaboration across the teams
 - Example:
   a. Developer – EC2 & S3 Access
   b. Tester – Read only CloudWatch
   c. Admin – Full access

B. Granular Permissions
 - IAM policies allow very specific permissions
 - Permission can be defined at:
    1. Service level – (EC2, S3, VPC)
    2. Action level – (Start instance, GetObject)
    3. Resource level – (Specific bucket, instance, EBS volume)
    4. Conditions like IP address restrictions
    5. MFA requirement, Time based access
 - Example: user can upload a file to Amazon-S3 but cannot delete them
 - why it matters:
      1. Follows least privillage principle
      2. Reduce security risk
     
C. MFA (Multi Factor Authentication)
 - MFA requires two authentication factors: password and one-time security code
 - Protects against stolen password
 - Strongly recommended for root & IAM users
  Example: Even if password is compromised attacker cannot login without MFA code

D. Free to use :
 - IAM has nop aditional cost
 - AWS doesn not charge for:
    user groups, roles, policies, MFA configuration
 - Why it matters
  1. Encourages strong security practices
  2. No financial barrier to access control

```

# IAM Resource Limits
```
1. IAM users per account → 5000
2. IAM groups per account → 300
3. Users per group → 1000
4. Groups per user → 10
5. Managed policies per user → 10
6. Inline policies per user → 1
7. Access key per user → 2
```

# IAM Identities

```
How IAM Identities Work Together in Steps :
  1. User or Role requests access
  2. IAM policies evaluate permissions
  3. Access is Allowed or Denied

1) IAM User
- Represents an individual person or application
- Permanent credentials (Password / Access Key)
- Can login to AWS console
- Permissions assigned directly or via group
- Used cases:
   Human users (Admin, developer, tester)
   Eg: Tester user with read-only access

2) IAM Group
- A collection of IAM users that share same permissions
- Permissions attached to group
- Key features:
   1. Permissions attached to group
   2. User inherit the permission
   3. Group cannot contain group/sub-group
 - Use-case:
    Team based control
    Eg: Developers group with EC2 & S3 access

3) IAM Role
- An identity with temporary credentials assumed by trusted entities
- No permanent credentials
- Used via trust policy
- Key features:
   1. No permanent credentials (Uses trust policy)
   2. Automatically rotated credentials
- Used cases:
   1. EC2 accessing S3
   2. Cross account access
   3. Lambda accessing DynamoDB
- Example: EC2 instance assume role to read S3 without access key

4) IAM Policy
- IAM policy is a JSON document which defines permissions
- Key feature:
  1. It specifies: Action, Resource, Conditions
  2. Can be AWS managed, customer managed, or Inline

```
