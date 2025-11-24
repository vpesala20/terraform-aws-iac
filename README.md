# 🚀 Terraform AWS Infrastructure Automation

A production‑ready Infrastructure‑as‑Code project that provisions a complete AWS environment using Terraform. This setup includes a VPC with public/private subnets, an Internet Gateway, NAT Gateway, EC2 compute layer, and an Application Load Balancer — fully automated, modular, and ready for CI/CD.

---

## 📌 **Architecture Overview**

This Terraform project deploys the following architecture:

* **VPC (10.0.0.0/16)**
* **2 Public Subnets** (web tier)
* **2 Private Subnets** (app/data tier)
* **Internet Gateway + NAT Gateway**
* **EC2 Web Server** (user‑data bootstrapped)
* **Application Load Balancer (ALB)**
* **Security Groups** for ALB + EC2
* **Outputs for ALB DNS, EC2 ID, Subnet IDs, VPC ID**

---

## 📂 **Project Structure**

```
terraform-aws-iac/
├── backend.tf
├── main.tf
├── variables.tf
├── outputs.tf
├── provider.tf
└── modules/
    ├── vpc/
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    ├── ec2/
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    └── alb/
        ├── main.tf
        ├── variables.tf
        └── outputs.tf
```

---

## 🧩 **Modules Breakdown**

### **🔹 VPC Module**

Creates networking resources:

* VPC
* Public + Private Subnets
* Internet Gateway
* NAT Gateway
* Route Tables + Associations

### **🔹 EC2 Module**

Deploys:

* Web Server (Amazon Linux / Ubuntu)
* User‑data for basic web content
* Instance profile, EBS volume
* Web security group (HTTP + SSH)

### **🔹 ALB Module**

Creates:

* Application Load Balancer
* Target Group
* Listener (port 80)
* Target group attachment to EC2

---

## 🧪 **How to Run the Project**

### 1️⃣ Initialize Terraform

```
terraform init
```

### 2️⃣ Validate

```
terraform validate
```

### 3️⃣ View the plan

```
terraform plan
```

### 4️⃣ Apply infrastructure

```
terraform apply -auto-approve
```

---

## 📤 **Outputs**

Terraform returns:

* **VPC ID**
* **Public Subnet IDs**
* **Private Subnet IDs**
* **Internet Gateway ID**
* **NAT Gateway ID**
* **EC2 Instance ID**
* **ALB DNS Name**

Example:

```
vpc_id                 = "vpc-xxxx"
public_subnet_ids      = ["subnet-a", "subnet-b"]
private_subnet_ids     = ["subnet-c", "subnet-d"]
internet_gateway_id     = "igw-xxx"
nat_gateway_id          = "nat-xxx"
web_instance_id         = "i-xxxx"
alb_dns                 = "web-alb-xxxx.elb.amazonaws.com"
```

---

## 🛠️ **Technologies Used**

* Terraform
* AWS VPC, EC2, ALB, IAM
* Git & GitHub
* Infrastructure-as-Code (IaC)

---

## 🏗️ **Future Enhancements**

* Add CI/CD (GitHub Actions: fmt + validate + plan)
* Add Auto Scaling Group
* Add RDS module
* Add S3 + DynamoDB remote backend
* Add CloudWatch monitoring module

---
