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
