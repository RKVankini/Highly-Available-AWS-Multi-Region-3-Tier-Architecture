# 🚀 Highly Available AWS Multi-Region 3-Tier Architecture

This repository documents the implementation of a **Highly Available, Multi-Region 3-Tier Application Architecture on AWS**.

The project was developed in phases — starting with a core 3-tier deployment and later extended with **Auto Scaling, Route 53 failover, cross-region disaster recovery, CloudFront, and WAF protection** to simulate real-world production infrastructure.

------------------------------------------------------------

## 🏗️ Architecture Overview

![Architecture Diagram](architecture.gif)

The architecture follows a **Warm Standby Disaster Recovery strategy** using two AWS regions:

- **Primary Region:** us-east-1 (N. Virginia)
- **Disaster Recovery Region:** us-west-2 (Oregon)

------------------------------------------------------------

## 🧱 3-Tier Architecture

1. **Presentation Layer**
   - React frontend served via Application Load Balancer
   - CloudFront CDN for global delivery and failover

2. **Application Layer**
   - Node.js backend running on EC2 instances
   - Managed by Auto Scaling Groups
   - Traffic routed via Application Load Balancer

3. **Database Layer**
   - Amazon RDS MySQL (Multi-AZ) in private subnets
   - Cross-region read replica for disaster recovery

------------------------------------------------------------

## ☁️ AWS Services Used

- Amazon VPC (Multi-AZ, Public & Private Subnets)
- Internet Gateway & NAT Gateway
- EC2, Launch Templates & Auto Scaling Groups
- Application Load Balancers (Frontend & Backend)
- Amazon RDS (Multi-AZ + Read Replica)
- Amazon Route 53 (Failover Routing & Health Checks)
- Amazon CloudFront (Origin Failover)
- AWS WAF (Web Application Firewall)
- AWS Certificate Manager (ACM)
- AWS Backup
- Amazon CloudWatch

------------------------------------------------------------

## ⚙️ Key Features Implemented

- Multi-AZ VPC design in both regions
- Auto Scaling for frontend and backend tiers
- Secure private subnet database access
- Route 53 DNS failover between regions
- CloudFront origin failover for frontend
- HTTPS using ACM certificates
- WAF protection against common web threats
- Manual DR testing by simulating regional outages
- Bastion host for secure private access
- Complete resource cleanup strategy

------------------------------------------------------------

## 📁 Project Structure

backend/                    Node.js backend application  
client/                     React frontend application  
mysql/                      Database scripts  
rds/                        RDS related configuration  
terraform_main_ec2/         EC2 & networking automation  
eks-terraform/              Kubernetes setup (optional)  
kubernetes-files/           Kubernetes manifests  
Jenkins-Pipeline-Code/      CI/CD pipeline scripts  
docker-compose.yaml         Local development setup  
architecture.gif            Architecture diagram  
README.md

------------------------------------------------------------

## 📘 Detailed Documentation

A complete **step-by-step implementation guide with screenshots**, including:
- VPC & subnet setup
- Security groups
- RDS Multi-AZ & read replica
- Auto Scaling Groups
- Route 53 failover records
- CloudFront origin groups
- WAF rules
- Disaster recovery testing
- Resource cleanup

is available in the attached **project PDF documentation**.

------------------------------------------------------------

## 🎯 Learning Outcomes

- Designed a production-style multi-region AWS architecture
- Implemented high availability and disaster recovery
- Gained hands-on experience with Route 53 failover
- Understood CloudFront origin failover behavior
- Applied security best practices using WAF and private subnets
- Tested real disaster recovery scenarios

------------------------------------------------------------

## ✅ Final Note

This project represents an **end-to-end AWS Cloud & DevOps learning journey**, covering infrastructure design, scalability, security, and disaster recovery using AWS best practices.

Thank you for exploring the project 🙂 
