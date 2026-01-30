# Highly Available AWS Multi-Region 3-Tier Architecture

This repository demonstrates the design and deployment of a highly available, scalable, and secure 3-tier application architecture on AWS using real-world DevOps and Cloud best practices.

The application is structured into three layers: Presentation, Application, and Database, and is deployed using Infrastructure as Code, CI/CD pipelines, and containerization.

------------------------------------------------------------

Architecture Overview

![Architecture Diagram](architecture.gif)

------------------------------------------------------------

Tech Stack

Application:
- React.js
- Node.js
- MySQL

Cloud & DevOps:
- AWS (EC2, VPC, RDS, ALB, Route 53)
- Terraform (Infrastructure as Code)
- Docker & Docker Compose
- Kubernetes (EKS)
- Jenkins (CI/CD)
- PM2 (Node.js Process Manager)

------------------------------------------------------------

Project Structure

Highly-Available-AWS-Multi-Region-3-Tier-Architecture

backend/                    Node.js backend service  
client/                     React frontend  
mysql/                      Database scripts  
rds/                        RDS configuration  
terraform_main_ec2/         Terraform for EC2-based infrastructure  
eks-terraform/              Terraform for EKS cluster  
kubernetes-files/           Kubernetes manifests  
Jenkins-Pipeline-Code/      Jenkins CI/CD pipelines  
docker-compose.yaml         Docker Compose setup  
architecture.gif            Architecture diagram  
README.md

------------------------------------------------------------

Prerequisites

- AWS Account
- Terraform installed
- Node.js installed (https://nodejs.org)
- Docker & Docker Compose (optional)
- Basic knowledge of AWS and Linux

------------------------------------------------------------

High-Level Deployment Flow

1. Create VPC with public and private subnets
2. Deploy MySQL RDS in private subnets
3. Launch backend servers in private subnets
4. Configure Application Load Balancers in public subnets
5. Deploy frontend using Apache web server
6. Connect frontend to backend and database
7. Automate deployments using Terraform and Jenkins

------------------------------------------------------------

Backend Setup

1. Clone Repository

git clone https://github.com/RKVankini/Highly-Available-AWS-Multi-Region-3-Tier-Architecture.git
cd backend

2. Configure Environment Variables

Create .env file inside backend directory

DB_HOST=your-rds-endpoint
DB_USERNAME=admin
DB_PASSWORD=your_password
PORT=3306

3. Database Initialization

sudo yum install mariadb105-server -y
mysql -h your-rds-endpoint -u admin -p < test.sql

4. Backend Deployment

sudo dnf install -y nodejs
npm install
npm install dotenv
npm install -g pm2

pm2 start index.js --name node-app
pm2 startup
pm2 save

Backend is now running behind the Application Load Balancer.

------------------------------------------------------------

Frontend Setup

1. Configure Backend API URL

Edit the following file:

client/src/pages/config.js

Update the API URL:

const API_BASE_URL = "http://<backend-load-balancer-dns>";

2. Build and Deploy Frontend

sudo dnf install -y nodejs
sudo yum install httpd -y

npm install
npm run build

sudo cp -r build/* /var/www/html
sudo systemctl start httpd
sudo systemctl enable httpd

Frontend is now accessible via the Frontend Load Balancer.

------------------------------------------------------------

CI/CD Pipeline

Jenkins is used to automate build, test, and deployment processes.

Pipeline configurations are available in:

Jenkins-Pipeline-Code/

------------------------------------------------------------

Key Highlights

- Highly Available AWS Architecture
- Secure Private Subnet Database
- Infrastructure as Code using Terraform
- CI/CD Automation with Jenkins
- Containerized and Kubernetes-ready
- Real-world production design

------------------------------------------------------------

Learning Outcomes

- AWS Networking and Load Balancing
- Terraform module-based infrastructure
- Secure RDS deployment
- Production-grade Node.js deployment
- CI/CD pipeline implementation
- End-to-end DevOps workflow

------------------------------------------------------------

Thank you for exploring this project.
