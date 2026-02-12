
# 🌐 Networking and Subnetting 
##  IP Address Types
There are two main types of IP addresses:
  1.IPv4
  2.IPv6

## IPv4 Explanation
```
- IPv4 is a **32-bit number**
- It uniquely identifies a device on a network
- Written in **decimal format**
- Divided into **4 octets**
- Each octet = **8 bits**
- Format:
   8 bit + 8 bit + 8 bit + 8 bit = 32 bits
- Range:Each octet ranges from 0 → 255
- Example:192.168.1.10
```
## IPv4 Classes (Classful Addressing)
```
There are 5 IP Classes:
 Class A – Large Network
  - Range: 0 – 126
  - IP Range: 0.0.0.0 – 126.255.255.255
  - Format: N – H – H – H
  - Supports ~16–17 million hosts
  Example:10.0.0.0

 Class B – Medium Network
  - Range: 127 – 191
  - IP Range: 127.0.0.0 – 191.255.255.255
  - Format: N – N – H – H
  - Supports ~65,000 hosts
  - Example: 172.16.0.0/16

 Class C – Small Network
  - Range: 192 – 223
  - IP Range: 192.0.0.0 – 223.255.255.255
  - Format: N – N – N – H
  - Supports 254 hosts
  -Example:192.168.10.0/24

 Class D
  - Range: 224 – 239
  - Used for **Multicasting**

 Class E
  - Range: 240 – 255
  - Reserved for research purposes
```
## Public vs Private IP
 ```
 1. Public IP
  - Dynamic
  - Used on the internet
 2.Private IP
  - Static (inside private network)
  - Used inside LAN/VPC
```
Private IP ranges:

| Class | Private Range                 |
| ----- | ----------------------------- |
| A     | 10.0.0.0 – 10.255.255.255     |
| B     | 172.16.0.0 – 172.31.255.255   |
| C     | 192.168.0.0 – 192.168.255.255 |

---

## Binary Basics (Important for Subnetting)
8-bit values:
| Bit Position  | 1   | 2  | 3  | 4  | 5 | 6 | 7 | 8 |
| ------------- | --- | -- | -- | -- | - | - | - | - |
| Binary Weight | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
```
Total Sum of 8 Bits:
 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255
 Each octet is calculated using these binary weights.
```
##  CIDR (Classless Inter-Domain Routing)
```
CIDR format:0.0.0.0/n
 Where: n = number of network bits
        Remaining bits = host bits

## Formula: Total IPs = 2^(32 - CIDR)
```


## CIDR Block Size Calculation

Powers of 2:

```
2¹ = 2
2² = 4
2³ = 8
2⁴ = 16
2⁵ = 32
2⁶ = 64
2⁷ = 128
2⁸ = 256
2⁹ = 512
2¹⁰ = 1024
2¹¹ = 2048
2¹² = 4096
```

---

# 8️⃣ Example – Create VPC

VPC CIDR:

```
192.168.0.0/16
```

Name: VPC01

---

# 9️⃣ Subnet Example
```
Subnet: 192.168.0.0/22

Total IPs: 32 - 22 = 10
           2¹⁰ = 1024 IPs
```
Binary Conversion of /22:

| 11111111   |       11111111   |     11111100     |    00000000   |
|------------|------------------|------------------|---------------|
|  8         |           8      |       6-2        |     8         |             
| Network    |        Network    |    Net - Host     |       Host     |


/22 means:

* 22 bits ON (network bits)
* Remaining OFF (host bits)

---

## Magic Number Method

   Magic number formula:
```
  256 - subnet mask value

For /22:
Subnet mask: 255.255.252.0

Magic number: 256 - 252 = 4

So subnet ranges increase by 4.

Example subnets:
192.168.0.0 – 192.168.3.255
192.168.4.0 – 192.168.7.255
192.168.8.0 – 192.168.11.255
```


## Question Example

### Q) 172.16.0.0/20 – How many IPs?
```
32 - 20 = 12
2¹² = 4096 IPs

Answer: 4096 IP addresses
```
### Q) If you want to deploy 64 servers, what CIDR?
```
64 = 2⁶
So n = 6 host bits

CIDR calculation:
32 - 6 = 26

Required subnet: /26
```

## Summary Formula Sheet
```
- Total IPs = 2^(32 - CIDR)
- Magic Number = 256 - subnet value
- Hosts required = 2^n
- CIDR = 32 - n
```


