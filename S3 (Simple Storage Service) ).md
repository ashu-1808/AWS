
#  Amazon S3


## Amazon S3 – Storage Classes 
```
1. S3 Standard
- Used for frequently accessed data
- High performance and low latency
- Durability: 99.999999999% (11 9’s)
- Availability: 99.99%
- Storage cost is higher
- Retrieval cost is very low
👉 Example: Websites, applications, active data

2. S3 Standard – IA (Infrequent Access)
- For data accessed less frequently
- Lower storage cost than Standard
- Retrieval charges apply
- Durability: -99.999999999-
- Availability: 099.9%
👉 Example: Backups, long-term storage

---

3. S3 Intelligent-Tiering
- Automatically moves data between tiers based on usage
- Saves cost automatically
- No retrieval fees
- Durability: 99.999999999%
- Availability: 99.9%
👉 Best when access pattern is unknown

4. S3 One Zone – IA
- Data stored in **single Availability Zone**
- Lower cost than Standard-IA
- Retrieval charges apply
- Durability: -99.999999999%
- Availability: -99.5%
👉 Example: Secondary backups, non-critical data


5.S3 Glacier (Archive Storage)*

 a. S3 Glacier Instant Retrieval
  - Archive data but needs immediate access
  - Retrieval in milliseconds
  - Up to 68% cheaper than Standard-IA
  - Durability: 99.999999999%
  👉 Example: Medical images, media archives

 b. S3 Glacier Flexible Retrieval
  - For archive data accessed 1–2 times per year
  - Retrieval time: Minutes to hours
  - Lower cost than Instant Retrieval
  👉 Example: Backup archives

 c. S3 Glacier Deep Archive
  - Cheapest S3 storage class
  - For data rarely accessed (once a year or less)
  - Retrieval time: Around 12 hours
  - Designed for long-term retention (7–20+ years)
  👉 Example: Compliance records, old financial data

```

![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/e7cf2f64449efbdfff60d1468816ef30d1859d9f/storage%20class.webp)

