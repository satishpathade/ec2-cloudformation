# AWS CloudFormation Template — EC2 in Custom VPC (Singapore Region)

This CloudFormation template sets up a **complete environment** to launch an EC2 instance inside a custom VPC in the **Singapore (ap-southeast-1) region** with HTTP and SSH access.  

It automatically creates all necessary networking resources so your EC2 instance is ready to use immediately.

---

## ⚙️ What This Template Does

When deployed, this template creates:

- **Custom VPC** with DNS support and hostnames enabled.
- **Public Subnet** with automatic public IP assignment.
- **Internet Gateway** attached to the VPC for internet access.
- **Route Table** with a route to the internet.
- **Security Group** allowing SSH (port 22) and HTTP (port 80).
- **EC2 Instance** (t2.micro) with a public IP and HTTP access.

---

## 📌 Resources Created

| Resource                         | Description |
|----------------------------------|-------------|
| `MyVPC`                          | Virtual Private Cloud with CIDR `10.0.0.0/16` |
| `MyInternetGateway`              | Internet Gateway for internet connectivity |
| `MyPublicSubnet`                 | Public subnet inside the VPC |
| `MyRouteTable`                   | Route table with internet route |
| `MySubnetRouteTableAssociation`  | Associates subnet with the route table |
| `MySecurityGroup`                | Security group allowing SSH & HTTP |
| `MyEC2Instance`                  | EC2 t2.micro instance with public IP |

---

## 🚀 Prerequisites

Before deploying, ensure you have:

- An **AWS account**.
- AWS CLI or AWS Management Console access.
- **AMI ID** valid in Singapore region (`ami-088d74defe9802f14` change your id).
- **EC2 Key Pair** created in your AWS account (`web-serverkey` your key-pair).

---

## 🛠 Deployment Instructions

### Using AWS Management Console
1. Open the **CloudFormation** service.
2. Click **Create Stack → With new resources (standard)**.
3. Upload `ec2-template.yaml`.
4. Follow the prompts and click **Create Stack**.

### Using AWS CLI
```bash
aws cloudformation create-stack \
  --stack-name ec2-autolounch \
  --template-body file://ec2-lounch.yaml \
  --region ap-southeast-1 \
  --capabilities CAPABILITY_NAMED_IAM
