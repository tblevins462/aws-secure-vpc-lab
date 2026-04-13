# AWS Secure VPC Lab
Documentation in progress — screenshots and architecture coming soon.

## Step 1 — VPC Creation

Created a new VPC named `secure-vpc-lab-vpc` using CIDR block `10.0.0.0/16`.  
This provides a large address space for multiple subnets and future expansion.

**Screenshot:**  
See `screenshots/01-vpc-created.png`

## Step 2 — Public and Private Subnets

Created two subnets within the VPC:

### Public Subnet
- Name: `public-subnet-1`
- CIDR: `10.0.1.0/24`
- Auto-assign public IPv4 enabled for internet-facing resources

### Private Subnet
- Name: `private-subnet-1`
- CIDR: `10.0.2.0/24`
- No public IP assignment for improved security

**Screenshots:**  
- `screenshots/02-public-subnet.png`  
- `screenshots/03-private-subnet.png`

## Step 3 — Internet Gateway

Created an Internet Gateway (`secure-vpc-lab-igw`) and attached it to the VPC (`secure-vpc-lab-vpc`).  
This enables internet connectivity for resources placed in the public subnet.

**Screenshot:**  
- `screenshots/04-internet-gateway.png`

## Step 4 — Route Tables
Created a public route table (`secure-vpc-lab-rtb-public`) and associated it with the public subnet. Added a default route (`0.0.0.0/0`) pointing to the Internet Gateway to enable outbound internet access for public resources. Created a private route table (`secure-vpc-lab-rtb-private1-us-east-1a`) and associated it with the private subnet for isolated internal routing.

**Screenshots:**  
- `screenshots/05-public-route-table.png`  
- `screenshots/06-private-route-table.png`

  ## Step 5 — NAT Gateway
Created a NAT Gateway (`secure-vpc-lab-natgw`) in the public subnet and attached an Elastic IP address. Updated the private route table to route `0.0.0.0/0` traffic to the NAT Gateway. This allows private subnet resources to securely access the internet for updates and external services without exposing them to inbound public traffic.

**Screenshot:**  
- `screenshots/07-nat-gateway-route.png`

## Step 6 — Security Groups
Created two security groups to enforce least‑privilege access across the VPC. The public security group allows inbound SSH access only from my IP address, ensuring secure access to the public‑facing instance. The private security group allows inbound SSH access only from the public security group, preventing any direct access from the internet and maintaining strict isolation for private subnet resources.

Screenshot:
screenshots/08-security-groups.png
