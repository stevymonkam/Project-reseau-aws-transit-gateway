# AWS Cloud Engineer Bootcamp Project

## Network Management

### Objectives
The objective of this project is to implement a robust and secure cloud network architecture within AWS.

![](reseaupng)


![](cout.png)

---

## Solution: Deploying Our Stack on AWS

### Step 1: Create the Base Image Template
1. Go to **AWS Services > EC2 > Launch an instance**.
2. Launch an instance using the default parameters.
3. Connect to the instance and start server configuration.
4. Use the provided `script.sh` file.
5. Create an IAM role for access to **CloudWatch** and **SSM**.

### Step 2: Create VPCs and Subnets
#### 1. Create VPCs
- Log in to the AWS console.
- Navigate to **VPC > Create VPC**.
- Create two separate **VPCs** with unique CIDR blocks:
  - `VPC1` → **10.0.0.0/16**
  - `VPC2` → **10.1.0.0/16**

#### 2. Create Subnets
For **VPC1**:
- Public Subnet: **10.0.1.0/24**
- Private Subnet: **10.0.2.0/24**

For **VPC2**:
- Public Subnet: **10.1.1.0/24**
- Private Subnet: **10.1.2.0/24**

### Step 3: Configure Routing Tables & Gateways
#### 1. Internet Gateway (IGW)
- Create an **Internet Gateway (IGW)** and attach it to **VPC1**.
- Repeat the same for **VPC2**.

#### 2. Route Tables
- Create a **Public Route Table** for **VPC1** and associate it with `PublicSubnet1`.
- Create a **Public Route Table** for **VPC2** and associate it with `PublicSubnet2`.
- Configure NAT Gateways for **private subnets**.

### Step 4: Configure Transit Gateway
1. Create a **Transit Gateway (TGW)**.
2. Attach both VPCs to the **Transit Gateway**.

### Step 5: Launch Instances & Configure Bastion
1. **Launch a Bastion Host** in `PublicSubnet1`.
2. **Launch Application Instances** in private subnets (`PrivateSubnet1`, `PrivateSubnet2`).

### Step 6: Configure Load Balancer & Auto Scaling
1. Create a **Network Load Balancer (NLB)**.
2. Configure an **Auto Scaling Group** for the application instances.

### Step 7: Configure VPN & CloudWatch
1. (Optional) Configure a **VPN Connection**.
2. Set up **CloudWatch Alarms** for monitoring.

### Step 8: Configure AWS WAF
1. Create an **IP Set** and define blocked IP ranges.
2. Configure **Web ACL Rules** using AWS-managed rules.

### Step 9: Configure Route 53
1. Set up a **hosted zone** in Route 53.
2. Create an **Alias record** pointing to the **Load Balancer**.
3. Update your domain registrar with the **NS records** from Route 53.

---

## Conclusion
Following these steps, you should be able to set up the described architecture using AWS Console. The setup includes creating VPCs, subnets, routing tables, gateways, a Transit Gateway, VPN connections, Auto Scaling Groups, and Load Balancers.

Happy Cloud Engineering! 🚀
