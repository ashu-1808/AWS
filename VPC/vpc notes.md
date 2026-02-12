

#  VPC (Virtual Private Cloud)
```
- VPC is a virtual network inside AWS for one client
- VPC is virtual cloud for private client
- It is logically isolated from other network in AWS cloud
- Make 5 VPC can be created in one region
- 200 subnet in 1 VPC
- Once we created VPC then DHCP NACL and security group will be created automatically
- Once VPC is created you cannot change CIDR block range
- If you need different CIDR size then create new VPC
- Different subnet within a VPC cannot overlap

```


## DHCP (Dynamic Host Configuration Protocol)
```
Types of VPC → 1. Default VPC
               2. Custom VPC
```
![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/e13cb76891f22c79b7d06a14897306dfbc079ab3/VPC/DefaultVPC-vs-CustomVPC.jpg)


## Steps to Create VPC
```
1. Create VPC
2. Create subnet
3. Create Internet gateway & attach to VPC
4. Create and edit route table
5. Go in subnet association & add route table
6. Add edit route → add 0.0.0.0 to my IGW
```


## Subnet
```
- Subnet is a range of an IP address in a VPC
- Subnetting is a process of dividing larger network into smaller one
- One VPC can contain upto 200 subnet
- Subnet is always created on availability zone
- Subnetting can reduce network congestion
```


## Types of Subnet
```
1. Public subnet:
 - If a subnet traffic is routed to an IGW then this subnet is known as public subnet
 - Public subnet has public IP address
2. Private subnet
- If subnet does not have a route to IGW then this subnet is known private subnet
- Private subnet has private IP address
```

## Internet Gateway (IGW)
```
- An IGW is a virtual cloud router that connects VPC to internet
- Default VPC is already attached with an IGW
- If you create a new VPC you must attach it to IGW to access the internet

```

## Route Table
```
- Route table is a central routing system function & it is used to route traffic to the internet gateway
- You can create upto 200 route table and you can have upto 50 route entries per route table
```


## NAT Gateway
```
- NAT gateway works for private subnet but it is available in public subnet
- NAT gateway is one way door, so outside traffic cannot initiate
- Only elastic IP is given to NAT gateway
- You will be charged for creating and using NAT gateway
- Before deleting a NAT gateway, disassociate its elastic IP address, but
  does not release address from your account, you have to release it manually
- We use NAT gateway so that instances in private subnet can connect to the
  services outside your VPC or internet but external services or internet
   cannot initiate a connection with those instances
- With NAT gateway private instances don’t need public IP address to reach internet

```
# Bastion Host
```
- It is a computer acting as a security gatekeeper
- It is essentially a jump server or jump base
- Acting as an intermediary for secure connection to resources
  within private network
- 8.8.8.8 = google DNS server
```


# VPC Security
```
1. Security Group
2. NACL (Network Access Control List)
```


## Difference between NACL & Security Group
![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/2276e5c262a573d4ad8f9a7766f131d8bbdc1938/VPC/NACL%26SC-GROUP.png)                             |
## notes
```
- If traffic is allowed in Security Group, response traffic is automatically allowed (because   it is stateful).
- In NACL, you must explicitly allow both inbound and outbound traffic.
```


# VPC Peering

* VPC peering is a network connection between 2 VPCs
* Peering connection

(VPC1 ↔ VPC2 ↔ VPC3)

---
