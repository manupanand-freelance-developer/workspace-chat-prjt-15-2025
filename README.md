


# 🗨️ Workspace Chat Application Deployment (Self-Hosted)

This project automates the **self-hosted deployment of Mattermost**, an open-source, secure workplace messaging platform. The stack leverages **Terraform**, **Ansible**, and **Vault** to provision and configure infrastructure on **AWS** in a secure, reproducible, and scalable way.

---

## 📦 Tech Stack

- **Mattermost** – Self-hosted, open-source Slack alternative
- **Terraform** – Infrastructure as Code (IaC) for AWS provisioning
- **Ansible** – Configuration management and app installation
- **HashiCorp Vault** – Secret management
- **AWS** – Cloud infrastructure provider (EC2, S3, VPC, etc.)

---

## 📁 Project Structure

```
workspace-chat-deployment/
│
├── terraform/                 # AWS infrastructure provisioning
│   └── main.tf
│
├── ansible/                   # Configuration and provisioning
│   ├── playbooks/
│   └── inventory/
│
├── vault/                     # Vault policies and initialization scripts
│   └── secrets/
│
├── scripts/                   # Helper scripts
│   └── bootstrap.sh
│
├── README.md                  # Project documentation
└── LICENSE
```

---

## 🚀 Deployment Overview

### 1. Infrastructure Provisioning (Terraform)

- VPC, subnets, security groups
- EC2 instances (App server, optionally DB)
- IAM roles and instance profiles

```bash
cd terraform
terraform init
terraform apply
```

### 2. Secret Management (Vault)

- Initializes Vault
- Stores secrets like DB passwords, Mattermost config tokens

```bash
vault server -config=vault/config.hcl
vault operator init
vault kv put secret/mattermost/db username="mmuser" password="securepass"
```

### 3. Configuration and App Deployment (Ansible)

- Installs dependencies (Docker, PostgreSQL if needed, Mattermost)
- Pulls secrets securely from Vault
- Configures Mattermost with environment variables

```bash
cd ansible
ansible-playbook -i inventory/hosts playbooks/site.yml
```

---

## 🔐 Security Features

- **Vault integration** for secure secrets management (DB credentials, access tokens)
- **Ansible Vault** (optional) for encrypting sensitive vars
- **IAM roles** with least privilege for EC2 instances
- **Security groups** with tightly scoped ingress/egress rules

---

## ⚙️ Requirements

- AWS CLI and access credentials
- Terraform >= 1.0
- Ansible >= 2.10
- HashiCorp Vault >= 1.9
- Python3 (for Ansible)

---

## 📌 Features

- 100% Infrastructure-as-Code
- Modular and extensible
- Secure by design (Vault, encrypted vars, IAM roles)
- Production-ready deployment for small to medium teams
- Easy redeployment and teardown

---

## 📈 Future Improvements

- CI/CD pipeline integration (e.g., GitHub Actions)
- External database support (e.g., RDS)
- Auto-scaling for Mattermost instances
- HTTPS and domain setup (e.g., using ACM + Route53)

---

## 🧾 License

GNU Public license v3 2025. See `LICENSE` file for more information.

---

## ✍️ Author

Crafted  by Manu P Anand
