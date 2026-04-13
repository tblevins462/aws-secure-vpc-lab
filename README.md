# AWS Secure VPC Lab

This project demonstrates the creation of a secure AWS VPC environment with public and private subnets, an Internet Gateway, a NAT Gateway, route tables, and EC2 instances configured for secure access. All screenshots are stored in the `screenshots/` directory.

---

### Step 1 — VPC Creation
Created a new VPC named `secure-vpc-lab-vpc` using CIDR block `10.0.0.0/16`, providing a scalable address space for multiple subnets and future expansion.

**Screenshot:**  
`screenshots/01-vpc-created.png`

---

### Step 2 — Public Subnet Creation
Created a public subnet named `public-subnet-1` using CIDR `10.0.1.0/24`.  
Enabled auto‑assign public IPv4 to support internet‑facing resources.

**Screenshot:**  
`screenshots/02-public-subnet.png`

---

### Step 3 — Private Subnet Creation
Created a private subnet named `private-subnet-1` using CIDR `10.0.2.0/24`.  
Disabled public IP assignment to ensure isolation from the internet.

**Screenshot:**  
`screenshots/03-private-subnet.png`

---

### Step 4 — Internet Gateway
Created an Internet Gateway (`secure-vpc-lab-igw`) and attached it to the VPC to enable outbound internet access for public resources.

**Screenshot:**  
`screenshots/04-internet-gateway.png`

---

### Step 5 — Public Route Table
Created a public route table (`secure-vpc-lab-rtb-public`) and associated it with the public subnet.  
Added a default route `0.0.0.0/0` pointing to the Internet Gateway.

**Screenshot:**  
`screenshots/05-public-route-table.png`

---

### Step 6 — NAT Gateway
Created a NAT Gateway (`secure-vpc-lab-natgw`) in the public subnet and attached an Elastic IP.  
This allows private instances to securely access the internet for updates without exposing them publicly.

**Screenshot:**  
`screenshots/06-nat-gateway.png`

---

### Step 7 — Private Route Table
Created a private route table (`secure-vpc-lab-rtb-private1-us-east-1a`) and associated it with the private subnet.  
Added a default route `0.0.0.0/0` pointing to the NAT Gateway.

**Screenshot:**  
`screenshots/07-private-route-table.png`

---

### Step 8 — EC2 Instances
Launched two EC2 instances:

**Public EC2 (Bastion Host)**  
- Subnet: Public  
- Public IP: Yes  
- Purpose: Secure SSH entry point into the VPC

**Private EC2**  
- Subnet: Private  
- Public IP: No  
- Purpose: Internal application server

**Screenshots:**  
`screenshots/08-ec2-bastion.png`  
`screenshots/09-ec2-private.png`

---

### Step 9 — SSH into Bastion Host
Verified SSH access from the local machine into the public EC2 instance using the key pair.

**Screenshot:**  
`screenshots/10-ssh-into-bastion.png`

---

### Step 10 — SSH from Bastion → Private EC2
Copied the key pair to the bastion host, adjusted permissions, and used it to SSH into the private EC2 instance using its private IP.  
This validated that the VPC, subnets, route tables, NAT Gateway, and security groups were all configured correctly.

**Screenshot:**  
`screenshots/11-ssh-into-private.png`

---

### Step 11 — Private Instance Internet Test
Ran `sudo yum update -y` on the private EC2 instance to confirm outbound internet access through the NAT Gateway.

**Screenshot:**  
`screenshots/12-private-instance-internet-test.png`

---

---

### Architecture Diagram

Below is a high‑level architecture diagram representing the secure VPC environment built in this lab. It includes the VPC, public and private subnets, Internet Gateway, NAT Gateway, route tables, and EC2 instances.

```
                +-----------------------------+
                |       AWS Region (us-east-1)|
                |                             |
                |   +---------------------+   |
                |   |   VPC 10.0.0.0/16   |   |
                |   |                     |   |
                |   |  +---------------+  |   |
Internet        |   |  | Public Subnet |  |   |
Gateway <------>|---|--| 10.0.1.0/24   |  |   |
(IGW)           |   |  +-------+-------+  |   |
                |   |          | Bastion  |   |
                |   |          | EC2      |   |
                |   |          +----------+   |
                |   |                     |   |
                |   |  +---------------+  |   |
                |   |  | Private Subnet|  |   |
                |   |  | 10.0.2.0/24   |  |   |
                |   |  +-------+-------+  |   |
                |   |          | Private  |   |
                |   |          | EC2      |   |
                |   |          +----------+   |
                |   |                     |   |
                |   +---------------------+   |
                |                             |
                +-----------------------------+

Key:
- Public Subnet routes 0.0.0.0/0 → IGW
- Private Subnet routes 0.0.0.0/0 → NAT Gateway → IGW
- SSH: Local → Bastion → Private EC2
```

---
