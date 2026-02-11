
# EC2 [Elastic Compute Cloud]
```
Amazon EC2 is a foundational service within the compute domain of AWS
It falls under IaaS
Using ec2 we can create virtual machine
virtualmachine / Instance / VM / server
EC2 is a region specific service
You can create 20 instances per region
```
## steps to create Instance *
```
1.Tag – Key-value pair used to identify and organize resources.
2.AMI (Amazon Machine Image) – Template with OS and software to launch an instance.
3.Instance Type – Combination of CPU and RAM capacity.
4.Security Group – Virtual firewall that controls instance traffic.
5.Storage – Disk type used (HDD or SSD).
6.Key Pair – Used for secure instance login.
 types:
   public Key – Stored in AWS.
   Private Key – Downloaded by user.
```
## Types of instance state:
```
Stop – Shuts down instance.
Start – Powers on instance.
Reboot – Restarts instance.
Hibernate – Stops and saves RAM state.
Terminate – Deletes instance permanently.
Running – Instance is active.
Pending – Instance is launching.
```
## Check status:
```
- Detect the problem that may appear
- Status check are basically Health checks
- 2/2 = all okay
- 1/2 = system is clear but instance not okay
  → To resolve this please reboot instance
- 0/2 = system and instance both are not okay
  → To resolve this please stop then restart instance
```
## Every instance has 2 ip address Public and private
```
A. Public IP Address
 -Used to communicate over the internet.
 -Assigned automatically when instance starts.
 -Changes after stop/start (dynamic).

B. Private IP Address
 -Used for communication within the same network (VPC).
 -Assigned inside the private network.
 -Remains same after stop/start (static).
```
## Security group :
```
While working on it you only work on Inbound Rule
1.Inbound rule → Incoming traffic
2.Outbound rule → outgoing traffic

Default setting :
Inbound rule : No Rule
Outbound rule : Traffic allowed

Source Type :
You cannot block anyone but you can customize or add IP address which can access
 1.Anywhere : Everyone
 2.Custom : Can customize who can access
 3.My IP : Only owner
```
## SSH (Secure Shell)
 ```
 -Network communication protocol used to connect EC2 instance remotely.
 -Used because communication between host and client is encrypted.
 -Provides secure command-line access.
 -Works on Port 22 (Linux).
 -Security group changes apply immediately.
```
## Steps to Connect Linux EC2 Instance (SSH)
```
 1.Launch a Linux EC2 instance.
 2.Select the instance and click Connect.
 3.Choose the SSH Client option.
 4.Open Terminal (Git Bash / CMD / Linux terminal).
 5.Go to the folder where the .pem key is downloaded.
 6.Set permission: chmod 400 key.pem (for Linux/Mac).
 7.Copy the SSH command provided by AWS.
 8.Run the SSH command in terminal.
 9.Type yes (first time only).
```
## RDP (Remote Desktop Protocol)
 ```
 -Protocol that allows user to remotely access and control another computer.
 - Mainly used to connect to Windows servers.
 - Provides graphical desktop access.
 - Works on Port 3389 (Windows).
```
## Steps to Connect Windows EC2 Instance (RDP)
 ```
1.Launch a Windows EC2 instance.
 2.Select the instance and click Connect.
 3.Choose the RDP Client option.
 4.Download the Remote Desktop (.rdp) file.
 5.Click Get Password.
 6.Upload your private key (.pem) file.
 7.Decrypt the password and copy it.
 8.Open the downloaded .rdp file.
 9.Click Connect and enter the password.
 10.Click Yes to trust the certificate.

" Windows instance connected successfully ✅"
```
## While creating webserver you need to add http/https web-server
```
A.HTTP (HyperText Transfer Protocol)
1.Works on Port 80.
2.Used to transfer data between browser and server.
3.Data is not encrypted.
4.Less secure for communication.
5.URL starts with http://.

B.HTTPS (HyperText Transfer Protocol Secure)
1.Works on Port 443.
2.Secure version of HTTP.
3.Data is encrypted using SSL/TLS.
4.Provides secure communication between client and server.
5.URL starts with https://.
```

## Package management
```
-For downloading package you need to install package management tool
-Package management tool is software that helps you install, update, remove and manage
 software packages automatically on a operating system
-With systemctl you can start, stop, restart, check status and perform other advanced
 action on services
1.Yum : [Yellowdog Updater Modifier]
 → debian, ubuntu, mint, kali linux
2.apt : [Advanced Packaged Tool]
 → Red Hat Enterprise Linux [RHEL], CentOS
3.dnf : [Dandified YUM] faster replacement for yum.
 → Fedora, RHEL8+, centOS 8+
```
## http or https webserver apache (httpd):
```
 Apache (httpd) Web Server – Demo to Host Website on EC2
  -Apache is a web server used to host websites.
  -Service name in Linux is httpd.
  -Works on HTTP (80) and HTTPS (443).

Steps:
1.Create a Linux EC2 instance.
2.Allow HTTP (80) and HTTPS (443) in Security Group.
3.Connect to the instance using SSH.
4.Install Apache:
  → sudo yum install httpd -y
5.Start Apache service:
  → sudo systemctl start httpd
6.Enable Apache at boot:
  → sudo systemctl enable httpd
7.Check service status:
  → sudo systemctl status httpd
8.Create a sample webpage:
  → echo "This is my website!" > /var/www/html/index.html
9.Copy the Public IP in browser.

  Website hosted successfully on EC2 ✅
```

## SSH Configuration Demo (Ubuntu EC2) – Simple Steps
```
1.Launch Ubuntu EC2 instance.
2.Connect using SSH.
3.Switch to root:
 → sudo -i
4.Create new user:
 → adduser seema
5.Switch to user:
 → su - seema
6.Generate SSH key:
 → ssh-keygen
7.Check public key:
 → cat ~/.ssh/id_rsa.pub
( Copy and save it on your system.)
8.Create SSH folder (if not present):
 → mkdir -p ~/.ssh
9.Add public key to authorized_keys:
 → cp ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys
10.Set permission:
 → chmod 400 ~/.ssh/authorized_keys
11.Open MobaXterm :
   Start Session
   Remote session:(copy ip address of your instance)
   Advanced setting
   select seema-key.pemkey
   login as seema
 SSH configured successfully ✅
```

## instance purchase option































