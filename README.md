# AWS
AWS is a cloud platform that provides computing resources like servers, storage, databases, and networking over the internet on a pay-as-you-go basis.
## Cloud Computing :
Cloud computing is on demand delivery of compute power, database and other resources through a cloud provider via internet.

# Services in cloud:
```
1.IaaS → Infrastructure As A Service
2.PaaS → Platform As A Service
3.SaaS → Software As A Service
```
## IaaS vs PaaS vs SaaS comparison table
![image alt](https://github.com/ashu-1808/AWS/blob/60f612e4a53bcb45d539e218d6be90430b035f7b/iaas-paas-saas-comparison.jpg.optimal.jpg
)

## Drawbacks of cloud computing:
```
1.Cloud specialist skills
2.Downtime / Reliability
2.Restricted controls
4.Latency issue
5.Vendor Lockin
6.Hidden cost
```
## Cloud deployment models:
```
1.Public Cloud : AWS, AZURE, GCP : Globally
2.Private cloud : Enterprise Cloud IBM, Dell : Locally
3.Hybrid cloud : Netflix
```
## Hypervisor :
## What is a Hypervisor?
```
-A hypervisor is software that creates and manages virtual machines (VMs).
-It allows multiple virtual machines to run on a single physical server.
-It shares CPU, RAM, and storage between VMs.
```
![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/5fd65e50807bc4c46f1cda6c911bbd39c2ed40b0/hypervisor%20types.png)

| Feature          | Bare Metal                       | Hoasted (VM)                         |
| ---------------- | -------------------------------- | -------------------------------------------- |
| Definition       | Direct access to physical server | Virtual server running on physical hardware  |
| Hypervisor       | No hypervisor                    | Uses hypervisor                              |
| Performance      | Very high                        | Slightly lower (due to virtualization layer) |
| Resource Sharing | Not shared                       | Shared with other VMs                        |
| Cost             | Expensive                        | More cost-effective                          |
| Use Case         | High-performance workloads       | General applications & web hosting           |


## Virtualization :
```
-It helps in virtualization in AWS.
-It is a software that create and runs virtual machine.
-It is a technique simply the use of software to build virtual layer over hardware.
-allowing the hardware to be used more efficiently.
```

## About AWS :
```
- Nitro Hypervisor used by AWS before they used XEN.
- Default region in AWS is North-Virginia (us-east-1)
   North Virginia has 6 zones.
- Region: A region is a different geographical area like apsouth, useast,
   uswest and all regions are isolated from each other.
- Availability zone are physically separated data center within region
   and availability zone are also isolated from each other.
```





## 7 Layers of OSI Model (Top to Bottom)
```
7. Application Layer
 - Closest to end user
 - Provides network services to applications
 - Examples: HTTP, FTP, SMTP, DNS
 - Example: Opening a website in browser

6. Presentation Layer
 - Data formatting
 - Encryption / Decryption
 - Compression
 - Example: SSL/TLS encryption

5. Session Layer
 - Establishes, manages, and terminates sessions
 - Maintains connection between applications
 - Example: Login session on website

4. Transport Layer
 - End-to-end communication
 - Error handling
 - Flow control
 - Protocols: TCP, UDP
 - Example: Reliable data transfer using TCP

3. Network Layer
 - Logical addressing (IP address)
 - Routing of packets
 - Devices: Router
 - Protocol: IP

2. Data Link Layer
 - MAC addressing
 - Error detection
 - Devices: Switch
 - Protocol: ARP

1. Physical Layer
 -  Physical transmission of bits
 - Cables, wires, voltage signals
 - Devices: Hub, cables



📦 Data Flow Example
 1. Application → HTTP request
 2. Presentation → Encryption
 3. Session → Session established
 4. Transport → TCP segments
 5. Network → IP routing
 6. Data Link → Frame with MAC
 7. Physical → Bits on cable
 
```

![image alt](https://github.com/ashu-1808/AWS/blob/f4307431631f717353102e5594ea1b2c1c9cedf0/osi-model-7-layers-1.jpg)















