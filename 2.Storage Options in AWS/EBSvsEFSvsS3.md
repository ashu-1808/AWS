## EBS vs EFS vs S3 (Quick Comparison Table)
| Feature           | **EBS**                | **EFS**                        | **S3**                           |
| ----------------- | ---------------------- | ------------------------------ | -------------------------------- |
| **Storage Type**  | Block Storage          | File Storage                   | Object Storage                   |
| **Attach To**     | One EC2 instance       | Multiple EC2 instances         | Access via Internet (API/URL)    |
| **Availability**  | Single AZ              | Multi-AZ (Regional)            | Regional (Highly Durable)        |
| **Access Method** | Mounted as disk        | Mounted as shared file system  | Accessed via API/HTTP            |
| **Use Case**      | OS, Database           | Shared application files       | Backup, Static files, Archive    |
| **Scaling**       | Manual resize          | Automatic                      | Automatic                        |
| **Root Volume**   | Yes                    | No                             | No                               |
| **Best For**      | Boot disk & DB storage | Shared storage between servers | Unlimited storage & data archive |



![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/1aaf9e4bd3d1f33485bc888e6384938c05412a48/EBS%2CEFS%2CS3.png)
