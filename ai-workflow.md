### Step 1 — AI Assistance
Used AI to confirm best-practice CIDR sizing (/16 for VPC, /24 for subnets) and to help document the rationale clearly for recruiters and hiring managers.

### Step 2 — AI Assistance
Used AI to validate subnet sizing (/24) and confirm best practices for separating public and private resources.  
AI also helped structure documentation and ensure consistent naming conventions for clarity and recruiter readability.

### Step 3 — AI Assistance
Used AI to confirm the correct Internet Gateway configuration and verify that the IGW was properly attached to the VPC.  
AI also helped troubleshoot AWS console UI inconsistencies and ensured the IGW attachment was validated through the resource details page.
internet access.
Confirmed the final routing configuration and validated that the NAT Gateway was functioning as intended before moving to the next step.

### Step 4 — AI Assistance
Used AI to confirm the correct design and separation of public and private route tables and how each should be associated with the appropriate subnet. AI also helped validate that the public route table needed a 0.0.0.0/0 route to the Internet Gateway while the private route table should remain isolated until the NAT Gateway was introduced.

### Step 5 — AI Assistance
Used AI to understand proper NAT Gateway placement in a public subnet and why an Elastic IP is required for outbound internet access. AI also helped troubleshoot AWS console options (Zonal vs Regional, manual EIP selection) and verify that routing 0.0.0.0/0 from the private route table to the NAT Gateway would provide secure outbound-only internet connectivity for private resources.

### Step 6 — AI Assistance
Used AI to validate least‑privilege security group design and ensure proper isolation between public and private resources. AI helped confirm that the public security group should only allow SSH from my IP, while the private security group should only accept SSH from the public security group. AI also assisted in verifying that no 0.0.0.0/0 inbound rules existed on the private SG and that outbound rules remained open to support NAT Gateway egress.
