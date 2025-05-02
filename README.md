# SecureCloudOps – IAM & CloudWatch Monitoring Infrastructure (AWS, Terraform)

This project simulates a production-ready cloud monitoring and access control setup using **Terraform**, **AWS IAM**, and **CloudWatch**. It reflects real-world infrastructure used by fast-paced companies like **Inktel**, focusing on secure access, observability, and automation.

---

## Key Features

- **Infrastructure as Code (IaC)** using Terraform  
- **IAM Role & Instance Profile** for secure CloudWatch access  
- **CloudWatch Alarms** for CPU thresholds (overuse & underuse)  
- **Custom `config.json`** for CloudWatch Agent setup  
- **Modular & Scalable** layout for production readiness  
- **AWS Free Tier-compatible** deployment (t2.micro)

---

## Architecture Overview

- Launches a secure **Amazon Linux 2 EC2 instance**  
- Attaches an **IAM Role** with permission to publish metrics  
- Sets up **CloudWatch Alarms**:
  - CPU > 70% → Spike alert  
  - CPU < 10% → Idle warning  
- Prepares for integration with **SNS or Lambda** for alert automation

---

## Repository Structure

```
SecureCloudOps/
├── main.tf              # EC2 + CloudWatch alarm logic
├── iam.tf               # IAM Role, policy, and instance profile
├── variables.tf         # Variable declarations
├── terraform.tfvars     # Values like key_name, instance_type
├── output.tf            # Public IP + alarm outputs
├── config.json          # CloudWatch Agent config
├── .gitignore
└── .terraform.lock.hcl
```

---

## How to Deploy

1. Clone the project:
   ```bash
   git clone https://github.com/moebaker/SecureCloudOps.git
   cd SecureCloudOps
   ```

2. Update your variables:
   ```hcl
   key_name       = "cloudapp-key"
   instance_type  = "t2.micro"
   ```

3. Deploy the infrastructure:
   ```bash
   terraform init
   terraform plan
   terraform apply
   ```

4. Retrieve your instance’s public IP:
   ```bash
   terraform output instance_public_ip
   ssh -i ~/.ssh/cloudapp-key.pem ec2-user@<PUBLIC_IP>
   ```

---

## Real-World Use Case

This mirrors what companies deploy when they need:

- IAM-secured compute environments  
- Agent-based system metrics and health checks  
- Fast incident detection and resource optimization  
- DevOps practices in cloud security and monitoring

---

## Author

**Mohamed Baker**  
DevOps & Cloud Engineer  
[GitHub](https://github.com/moebaker) | moebaker954@gmail.com
