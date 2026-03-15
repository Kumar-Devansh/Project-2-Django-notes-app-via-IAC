# 🚀 Terraform AWS Infrastructure with VPC

This project provisions a complete AWS infrastructure using **Terraform Infrastructure as Code (IaC)**.
It automatically creates networking resources such as **VPC, subnets, routing, and compute infrastructure** required to deploy a scalable application environment.

---

# 📌 Project Overview

The goal of this project is to demonstrate how to build and manage AWS infrastructure using Terraform in a modular and automated way.

The infrastructure includes:

* Custom Virtual Private Cloud (VPC)
* Public and Private Subnets
* Internet Gateway
* Route Tables
* Security Groups
* EC2 Instances
* Automated Infrastructure Provisioning with Terraform

---

# 🏗️ Architecture

The infrastructure created by this Terraform code follows a typical cloud architecture:

```
                Internet
                    |
             Internet Gateway
                    |
                 AWS VPC
            -------------------
            |                 |
      Public Subnet      Private Subnet
            |                 |
          EC2 Instance    Application Resources
```

---

# 📂 Project Structure

```
terraform-project/
│
├── main.tf              # Main infrastructure configuration
├── variables.tf         # Input variables
├── outputs.tf           # Output values
├── provider.tf          # AWS provider configuration
├── terraform.tfvars     # Variable values
└── README.md            # Project documentation
```

---

# ⚙️ Prerequisites

Before running this project, ensure you have the following installed:

* Terraform
* AWS CLI
* Git
* AWS Account with appropriate IAM permissions

Configure AWS credentials:

```
aws configure
```

---

# 🚀 How to Deploy the Infrastructure

### 1️⃣ Clone the Repository

```
git clone https://github.com/Kumar-Devansh/Django-notes-app.git
cd Infrastructure
```

---

### 2️⃣ Initialize Terraform

```
terraform init
```

---

### 3️⃣ Validate Configuration

```
terraform validate
```

---

### 4️⃣ Preview Infrastructure Changes

```
terraform plan
```

---

### 5️⃣ Apply Infrastructure

```
terraform apply
```

Type **yes** when prompted.

---

# 🧹 Destroy Infrastructure

To delete all created resources:

```
terraform destroy
```

---

# 🔐 Security Best Practices

* Do not commit AWS credentials
* Use IAM roles wherever possible
* Store Terraform state securely (S3 + DynamoDB recommended)

---

# 🌟 Key Features

* Infrastructure as Code using Terraform
* Automated AWS resource provisioning
* Scalable VPC networking architecture
* Easy deployment and teardown
* Production-ready infrastructure structure

---

# 📚 Technologies Used

* Terraform
* AWS (VPC, EC2, Networking)
* Git & GitHub
* Infrastructure as Code (IaC)

---

# 👨‍💻 Author

**Kumar Devansh**

Cloud | DevOps | Infrastructure Automation

GitHub:
https://github.com/Kumar-Devansh

---

# ⭐ Support

If you found this project helpful, please consider **starring the repository**.
