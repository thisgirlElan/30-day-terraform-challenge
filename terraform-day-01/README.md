# 🏗️ Day 1: VPC, Subnets & Networking with Terraform

This project is part of my **30-Day Terraform Challenge**, where I’m learning Infrastructure as Code (IaC) by building and documenting in public.

For Day 1, I went beyond a simple EC2 setup and built a more complete AWS networking foundation using Terraform.

## ✍🏽 Blog

I documented my full Day 1 experience here:

👉🏽 [Read the Blog](https://buildwithelan.hashnode.dev/what-is-infrastructure-as-code-and-why-it-s-transforming-devops)

## 📌 What This Project Creates

This configuration provisions:

- A custom **VPC**
- **Public and Private Subnets** across multiple Availability Zones
- An **Internet Gateway** (for public access)
- A **NAT Gateway** (for private subnet outbound access)
- **Route Tables** for public and private traffic routing
- Route table **associations**
- Supporting resources like **Elastic IPs**

## 🧠 Architecture Overview (Simplified)
```text
VPC
├── Public Subnets
│ ├── Internet Gateway (IGW)
│ └── NAT Gateway
│
├── Private Subnets
│ └── Route through NAT Gateway
│
└── Route Tables
├── Public → IGW
└── Private → NAT
```

## 📁 Project Structure

```text
.
├── main.tf         # Core infrastructure definitions
├── variables.tf    # Input variables (region, CIDR, subnet configs)
├── .env    # Credentials file (not committed)

## ⚙️ Prerequisites

Make sure you have:

- Terraform installed
- AWS CLI installed
- AWS credentials configured

```bash
aws configure
```

## 🔐 Environment Variables (Recommended)

Instead of hardcoding credentials, export them:

```bash
export AWS_ACCESS_KEY_ID="<YOUR ACCESS KEY>"
export AWS_SECRET_ACCESS_KEY="<YOUR SECRET KEY>"
```

## 🚀 How to Run

1. Initialize Terraform
```bash
terraform init
```

2. Preview the infrastructure
```bash
terraform plan
```

3. Apply the configuration
```bash
terraform apply -auto-approve
```

## 🧹 Clean Up (Important 💸)

To avoid unnecessary AWS charges:
```bash
terraform destroy -auto-approve
```
## 🧠 Key Learnings

This lab helped me understand:

- How Terraform provisions network infrastructure, not just servers
- The difference between public vs private subnets
- How route tables control traffic flow
- Why NAT Gateways are needed for private subnet internet access
- That infrastructure has a lot of moving parts 😅

## ⚠️ Notes
- NAT Gateways can incur costs (remember to destroy resources after use)
- This setup is for learning purposes and may not reflect production best practices

## 📚 Resources & Attribution

This lab was inspired by and adapted from:

[hashicorp: Benefits of Iac Lab](https://github.com/btkrausen/hashicorp/blob/master/terraform/Hands-On%20Labs/Section%2002%20-%20Understand%20IAC%20Concepts/02%20-%20Benefits_of_Infrastructure_as_Code.md)

## 💬 Final Thought

This was my first time defining networking infrastructure end-to-end instead of clicking through AWS. 

It was actually fun.
