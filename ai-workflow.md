### Step 1 — AI Assistance
Used AI to confirm best-practice CIDR sizing (/16 for VPC, /24 for subnets) and to help document the rationale clearly for recruiters and hiring managers.

### Step 2 — AI Assistance
Used AI to validate subnet sizing (/24) and confirm best practices for separating public and private resources.  
AI also helped structure documentation and ensure consistent naming conventions for clarity and recruiter readability.

### Step 3 — AI Assistance
Used AI to confirm the correct Internet Gateway configuration and verify that the IGW was properly attached to the VPC.  
AI also helped troubleshoot AWS console UI inconsistencies and ensured the IGW attachment was validated through the resource details page.

## Step 4 — Route Tables (AI Workflow Notes)

Used AI to confirm the difference between public and private route tables and how each should be associated with subnets.
Verified with AI that the public route table requires a default route (`0.0.0.0/0`) pointing to the Internet Gateway.
Confirmed that the private route table should not point to the Internet Gateway and should remain isolated until the NAT Gateway is created.
Asked AI to validate naming conventions and ensure consistency across route table resources.
