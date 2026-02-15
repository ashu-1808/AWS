
# 🌍 CloudFront
---
## 🔹 What is CloudFront?

* It is a web service that gives business and web application developers an easy and cost-effective way to distribute content with low latency and high speed data transfer.
* CloudFront is a global service.
* CloudFront has 410+ Points of Presence in 90+ cities across 195 countries.
*  **Amazon CloudFront** is a global **Content Delivery Network (CDN)** service.
* It delivers content with **low latency and high transfer speeds**.
* Distributes content through a **global edge network** (Points of Presence).

---

## 🔹 Security Features

* Global service with **410+ edge locations** in 90+ cities across 195+ countries.
* Caches content at edge locations close to users.
* Supports **static & dynamic content**.
* Seamless integration with AWS services (S3, EC2, ALB, API Gateway).
* HTTPS (SSL/TLS encryption)
* DDoS protection via **AWS Shield**
* Geo-restriction (block specific countries)
* Signed URLs & Signed Cookies
* Origin Access Control (OAC) / OAI
* Mostly you do not enable WAF (Web Application Firewall).

---

## 🔹 Common Uses

* Amazon CloudFront is commonly used for:

  * Website acceleration
  * Video streaming
  * API acceleration
  * Secure global content delivery
  * Static website hosting
  * Media distribution

---

## 🔹 Performance
* Compression (Gzip/Brotli)
* It improves performance using HTTP/2, HTTP/3 & global edge network.
* It supports different price classes to balance cost and performance.

---

## 🔹 How CloudFront Works

1. User requests content.
2. Request goes to nearest **Edge Location**.
3. If cached → content served immediately.
4. If not cached → fetched from **Origin** (S3 / EC2 / ALB).
5. Content cached at edge for future requests.

---

## 🔹 Origins Supported

* Amazon S3 bucket
* EC2 instance
* Application Load Balancer
* API Gateway
* Custom origin (on-prem or external server)
---

## 🔹 Important Terms (Interview Focus)

| Term           | Meaning                                    |
| -------------- | ------------------------------------------ |
| Edge Location  | CloudFront data center that caches content |
| Origin         | Source of original content                 |
| Distribution   | CloudFront configuration                   |
| Cache Behavior | Rules to control caching                   |
| TTL            | Time to Live (cache duration)              |
| Invalidation   | Remove cached content manually             |

---

## 🔹 Advantages

* Low latency
* High availability
* Improved performance
* Global scalability
* Enhanced security

---
.

