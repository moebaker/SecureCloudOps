# SecureCloudOps
  A hands-on real-world AWS infrastructure automation project designed and executed by Mohamed Baker. This repository showcases my proficiency in Infrastructure as   Code (IaC), AWS EC2 provisioning, IAM security, CloudWatch observability, and basic cloud security automation workflows—all using Terraform, Linux CLI, and AWS CLI.

## Table of Contents:

  - [Overview](#overview)
  - [Tech Stack](#tech-stack)
  - [What I Built](what-I-built)
  - [Challenges I Solved](challenges-I-solved)
  - [CloudWatch Monitoring](CloudWatch-Monitoring)
  - [Skills Demonstrated](Skills-Demonstrated)
  - [Future Additions](Future-Additions)

## Overview

  Project Name: SecureCloudOps
  Duration: 2 daysObjective: Provision a secure, observable EC2 instance using Terraform, deploy and monitor a web service using NGINX, and automate metrics collection via the CloudWatch agent.
  
  This project simulates real-world DevOps responsibilities such as:
  
    - Infrastructure provisioning via Terraform
    
    - IAM policy/role management
    
    - CloudWatch metrics configuration
    
    - SSH-based debugging
    
    - Log collection and metric forwarding

## Tech Stack

  1. Cloud Services:
  
      - AWS EC2, IAM, CloudWatch, VPC
  
  2. IaC & Tools:
  
      - Terraform
      
      - Linux (Amazon Linux 2)
      
      - CloudWatch Agent CLI
      
      - SSH / SCP
  
  3. Other Tools Used:
  
      - Amazon Linux yum CLI tools
      
      - Visual Studio Code + integrated terminal

## What I Built

  1. Provisioned an EC2 instance with Terraform:
  
      - Used a Free Tier Amazon Linux 2 AMI
      
      - Created main.tf, variables.tf, outputs.tf, terraform.tfvars
      
      - Deployed with secure key pair (devops-key.pem)
  
  2. Defined custom security groups:
  
      - Allowed inbound SSH (port 22)
      
      - Allowed HTTP (port 80) for NGINX access
  
  3. Installed NGINX:
  
      - Accessed EC2 via SSH
      
      - Installed and verified NGINX with curl and public IP
  
  4. Created IAM Role + Instance Profile:
  
      - EC2CloudWatchAgentRole
      
      - Attached CloudWatchAgentServerPolicy
      
      - Bound instance profile to EC2
  
  5. Installed & configured CloudWatch agent:
  
      - Ran the CloudWatch wizard to create /opt/aws/.../config.json
      
      - Chose to monitor CPU, memory, disk, and swap
      
      - Launched agent with validated configuration
  
  6. Copied config back locally via SCP:
    
      - Used scp to transfer from EC2 to local project folder
      
      - Ensured reproducibility for version-controlled environments

## Challenges I Solved

  ### Issue & Fix
  
    - Terraform credential error                      - - Created IAM user with admin rights, ran aws configure
    
    - SSH timeout                                     - - Updated security group to allow inbound SSH from 0.0.0.0/0
    
    - Invalid Key Pair                                - - Ensured Terraform matched key name in AWS Console
    
    - SCP permission denied                           - - Corrected PEM file path and used correct local directory
    
    - CloudWatch agent not starting                   - - Ran fetch-config command and validated IAM role/profile attachment

## CloudWatch Monitoring   

  1. Enabled collection of metrics:
  
      - cpu_usage_user                              
      - mem_used_percent                                          
      - disk_used_percent                                
      - swap_used_percent
      
  2. Added EC2 dimensions: InstanceId, InstanceType, ImageId                           
  3. Configured interval: 60 seconds             
  4. Validated using amazon-cloudwatch-agent-ctl -a status


## Skills Demonstrated

    - Terraform scripting, validation, and provisioning
    
    - EC2, IAM, and key pair management
    
    - SSH access and troubleshooting
    
    - Installing and managing CloudWatch agent manually
    
    - Building reusable .json configs for observability
    
    - Debugging IAM, network rules, and system services
    
    - Docker container management and DB orchestration (outside project scope)

## Future Additions (EKS + GitOps)

    - To complete the Kubernetes section of my resume, upcoming goals include:
    
    - Deploying to AWS EKS with Helm
    
    - Using Kustomize for environment overlays
    
    - Setting up GitHub Actions to auto-deploy updates
    
    - Adding pod-level monitoring with Prometheus

# Summary

This project mimics real-world DevOps work that a 3-year engineer would perform. From provisioning to security, observability, and troubleshooting, it reflects depth in AWS + Terraform use cases.

